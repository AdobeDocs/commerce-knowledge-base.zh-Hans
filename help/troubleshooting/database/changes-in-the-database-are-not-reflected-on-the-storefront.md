---
title: 数据库中的更改未反映在店面上
description: 本文提供了避免在应用实体更新时出现延迟或中断的解决方案。 这包括如何避免更改日志表变得过大，以及如何设置 [!DNL MySQL] 表触发器。
exl-id: ac52c808-299f-4d08-902f-f87db1fa7ca6
feature: Catalog Management, Categories, Services, Storefront
role: Developer
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# 数据库中的更改未反映在店面上

本文提供了避免在应用实体更新时出现延迟或中断的解决方案。 这包括如何避免更改日志表变得过大，以及如何设置[!DNL MySQL]表触发器。

受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x

## 问题

您在数据库中所做的更改不会反映在店面上，或者在应用实体更新时出现严重延迟。 可能受影响的实体包括产品、类别、价格、库存、目录规则、销售规则和目标规则。

## 原因

如果索引器被[配置为按计划](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers)更新，则问题可能是由一个或多个更改日志过大或未设置MySQL触发器的表导致的。

### 超大的更改日志表

如果`indexer_update_all_views` cron作业多次未成功完成，则更改日志表将变得很大。

更改日志表是用来跟踪实体更改的数据库表。 只要不应用更改，记录就会存储在更改日志表中，该更改由`indexer_update_all_views` cron作业执行。 Adobe Commerce数据库中有多个更改日志表，它们按照以下模式命名： INDEXER\_TABLE\_NAME + &#39;\_cl&#39;，例如`catalog_category_product_cl`、`catalog_product_category_cl`。 您可以在我们的开发人员文档中的[索引概述> Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)一文中找到有关如何在数据库中跟踪更改的更多详细信息。

### [!DNL MySQL]数据库触发器未设置

如果在添加或更改实体（产品、类别、目标规则等）之后，没有向相应的更改日志表添加记录，则您可能会怀疑数据库触发器未设置。

## 解决方案

>[!WARNING]
>
>我们强烈建议在执行任何操作之前创建数据库备份，并在高站点负载期间避免执行这些操作。

### 避免更改日志表过大

确保`indexer_update_all_views` cron作业始终成功完成。

您可以使用以下SQL查询获取`indexer_update_all_views` cron作业的所有失败实例：

```sql
select * from cron_schedule where job_code = "indexer_update_all_views" and status
  <> "success" and status <> "pending";
```

或者，您可以通过搜索`indexer_update_all_views`条目来在日志中检查其状态：

* `<install_directory>/var/log/cron.log` — 适用于版本2.3.1+和2.2.8+
* `<install_directory>/var/log/system.log` — 对于早期版本

### 重新设置[!DNL MySQL]表触发器

要设置缺少的[!DNL MySQL]表触发器，您需要重新设置索引器模式：

1. 切换到“保存时”。
1. 切换回“按计划”。

使用以下命令执行此操作。

>[!WARNING]
>
>在切换索引器模式之前，我们建议将您的网站置于[维护](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=zh-Hans#maintenance-mode)模式和[禁用cron作业](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=zh-Hans#disable-cron-jobs)以避免数据库锁定。

```bash
php bin/magento indexer:set-mode {realtime|schedule} [indexerName]
```

>[!INFO]
>
>当索引器模式设置为调度时添加与索引器相关的数据库触发器，当索引器模式设置为实时时删除与索引器相关的数据库触发器。 如果在将索引器设置为计划期间数据库中缺少触发器，请将索引器更改为实时，然后将它们改回计划。 这将重置触发器。

## 相关阅读

* [[!DNL MySQL] 表在我们的支持知识库中太大](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-26945)
* 在我们的开发人员文档中[索引： [!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
