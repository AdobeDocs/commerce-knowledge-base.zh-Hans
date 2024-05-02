---
title: 数据库中的更改未反映在店面上
description: 本文提供了避免在应用实体更新时出现延迟或中断的解决方案。 这包括如何避免更改日志表过大，以及如何设置MySQL表触发器。
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# 数据库中的更改未反映在店面上

本文提供了避免在应用实体更新时出现延迟或中断的解决方案。 这包括如何避免更改日志表过大，以及如何设置MySQL表触发器。

受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x

## 问题

您在数据库中所做的更改不会反映在店面上，或者在应用实体更新时出现严重延迟。 可能受影响的实体包括产品、类别、价格、库存、目录规则、销售规则和目标规则。

## 原因

如果您的索引器为 [已配置为按计划更新](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html#configure-indexers)，该问题可能是由一个或多个更改日志过大或未设置MySQL触发器的表导致的。

### 超大的更改日志表

更改日志表会增长得很大，如果 `indexer_update_all_views` cron作业未成功完成多次。

更改日志表是用来跟踪实体更改的数据库表。 只要不应用更改，记录就存储在更改日志表中，该更改由 `indexer_update_all_views` cron作业。 Adobe Commerce数据库中有多个更改日志表，它们按照以下模式命名：例如INDEXER\_TABLE\_NAME + &#39;\_cl&#39; `catalog_category_product_cl`， `catalog_product_category_cl`. 有关如何在数据库中跟踪更改的更多详细信息，请参阅 [索引概述> Mview](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview) 本文档。

### MySQL数据库触发器未设置

如果在添加或更改实体（产品、类别、目标规则等）之后，没有向相应的更改日志表添加记录，则您可能会怀疑数据库触发器未设置。

## 解决方案

>[!WARNING]
>
>我们强烈建议在执行任何操作之前创建数据库备份，并在高站点负载期间避免执行这些操作。

### 避免更改日志表过大

确保 `indexer_update_all_views` cron作业始终成功完成。

您可以使用以下SQL查询获取 `indexer_update_all_views` cron作业：

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

或者，您可以通过搜索日志中的 `indexer_update_all_views` 条目：

* `<install_directory>/var/log/cron.log`  — 适用于版本2.3.1+和2.2.8+
* `<install_directory>/var/log/system.log`  — 对于早期版本

### 重新设置MySQL表触发器

要设置缺少的MySQL表触发器，需要重新设置索引器模式：

1. 切换到“保存时”。
1. 切换回“按计划”。

使用以下命令执行此操作。

>[!WARNING]
>
>在切换索引器模式之前，我们建议将您的网站置于 [维护](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode) 模式和 [禁用cron作业](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs) 以避免数据库锁定。

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>当索引器模式设置为调度时添加与索引器相关的数据库触发器，当索引器模式设置为实时时删除与索引器相关的数据库触发器。 如果在将索引器设置为计划期间数据库中缺少触发器，请将索引器更改为实时，然后将它们改回计划。 这将重置触发器。

## 相关阅读

<ul><li title="MySQL表太大"><a href="/help/troubleshooting/database/mysql-tables-are-too-large.md">MySQL表太大</a> 在我们的支持知识库中。</li>
<li title="MySQL表太大"><a href="https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html#m2devgde-mview">索引器概述&gt; Mview</a> 在我们的开发人员文档中。</li></ul>
