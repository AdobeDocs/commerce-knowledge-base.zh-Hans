---
title: 索引失效，并且“indexer_reindex_all_invalid”不断运行
description: 索引失效，并且“indexer_reindex_all_invalid”不断运行
labels: troubleshooting,error,indexing,crons,site performance,adobe commerce,magento,cron,indexer_reindex_all_invalid,SQL,MySQL,reindex
exl-id: c7148ef4-2155-4d4c-869b-1d08de4af598
feature: B2B, Catalog Management, Categories, Observability, Price Indexer
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# 索引失效，`indexer_reindex_all_invalid`不断运行

当网站因不断重新索引而出现性能问题时，本文会提供相应的可能解决方法。 这是由于[!DNL cron]作业`indexer_reindex_all_invalid`持续运行并在[!DNL reindex]上清理了缓存所导致。

## 受影响的产品和版本

* Adobe Commerce (cloud &amp; on-premises) 2.4.0+ (由于&#x200B;**[!UICONTROL Category Permissions]**&#x200B;是仅限Commerce的Adobe功能，因此不会影响Magento Open Source。)

## 问题

在[!DNL New Relic One]中，错误日志应显示`indexer_update_all_views`运行多次，时间> 1秒（即，它正在处理某些内容）。

## 原因

运行核心Adobe Commerce导入程序（手动或由[!DNL cron]运行）时，将执行一组跨多个核心模块的插件，以确定应该使哪些索引失效。

在[!DNL Commerce Admin]中启用&#x200B;**[!UICONTROL Category Permissions]**&#x200B;模块时出现问题。 如果为true，则模块插件在执行导入时始终使Product &amp; Category索引（以及链接索引）失效。 如果检查标准导入类型，则它们都会影响&#x200B;**[!UICONTROL Category Permissions]**。 预期无效。

此外，当站点启用了B2B模块时，如果激活了&#x200B;**[!UICONTROL Shared Catalog]**，它将打开并锁定&#x200B;**[!UICONTROL Category Permissions]**。 关闭&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;将解锁&#x200B;**[!UICONTROL Category Permissions]**，但不会将其关闭。

<u>正在检查[!DNL MySQL]数据库中的[!DNL cron]日志</u>：

如果您登录到[!DNL MySQL]数据库，他们可以查看`cron`日志中的&#x200B;**[!DNL reindex all indexes]**&#x200B;进程。
此&#x200B;**应该**&#x200B;出现很多次，但重要因素是该进程执行了两种可能操作之一。

该过程只能执行以下两项操作之一：

1. 无：0到1秒（1秒或更短） — 该进程检查它是否需要执行任何操作，如果它不需要执行任何操作，则停止。
1. [!DNL Reindex]所有内容：始终需要时间 — 通常为分钟。

通常情况下，您会希望看到流程多次出现，但执行时间小于1秒。
因此，商家可以使用此[!DNL MySQL]查询查找需要&#x200B;**超过1秒**&#x200B;才能运行的交易：

```sql
SELECT TIMESTAMPDIFF(SECOND, executed_at, finished_at) AS period FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' HAVING period > 1
```

通过运行以下命令，您可以查看期间记录时间：

```sql
SELECT executed_at FROM cron_schedule WHERE job_code = 'indexer_reindex_all_invalid' AND executed_at IS NOT NULL ORDER BY executed_at ASC LIMIT 1;
```

如果这没有给您足够长的时间来进行适当的评估，则可以在此[[!DNL Cron] （计划任务）](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html?lang=zh-Hans)指南之后增加在日志中保留成功的`cron`进程的时间，并增加&#x200B;**[!DNL Success History Lifetime]**&#x200B;值（默认值为60分钟）。


## 解决方案

扩展`Magento\CatalogPermissions\Model\Indexer\Plugin\Import`，使`afterImportSource`方法排除自定义导入程序。

```
    public function afterImportSource(\Magento\ImportExport\Model\Import $subject, $import)
    {
        if ($this->config->isEnabled() && $subject->getEntity() !== 'ENTITY_CODE') {
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Category::INDEXER_ID)->invalidate();
            $this->indexerRegistry->get(\Magento\CatalogPermissions\Model\Indexer\Product::INDEXER_ID)->invalidate();
        }
        return $import;
    }
```

其中，`ENTITY_CODE`是用于自定义导入器的`import.xml`文件中的实体名称参数的值。

## 相关阅读

Adobe Commerce操作配置指南中的[配置 [!DNL cron] 作业](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html?lang=zh-Hans)。
