---
title: 修复数据未在 [!DNL Commerce Data Exporter] 源中更新，并且 [!DNL cron] 日志中不存在更改日志表的错误
description: 本文提供了一个解决方案，用于修复在 [!DNL Commerce Data Exporter mview] 订阅中使用错误视图ID导致的数据同步问题。
feature: Data Import/Export, Saas, Logs
role: Developer
source-git-commit: cf87b5f1280a2d1d23c7ace37616feb337b5142f
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# 修复了[!DNL Commerce Data Exporter]源中未更新的数据，并且changelog表的[!DNL cron]日志错误不存在

本文提供了一个解决方案，用于修复在[!DNL Data Exporter] [[!DNL Mview]](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)订阅中使用错误视图ID导致的数据同步问题。 [!DNL Mview]订阅用于跟踪数据库表的更改。

## 受影响的产品和版本

已将自定义代码应用于数据导出功能的Adobe Commerce实例（`commerce-data-exporter`或`saas-exporter`）。 如果安装的[[!DNL SaaS] Data Export版本为103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-6)或更高版本，并且代码直接引用`catalog_data_exporter_products`索引，则会发生此错误。

## 问题

商家可能会发现目录[!DNL Data Exporter]馈送表中缺少数据更新，并在[!DNL cron]作业日志中看到以下错误：

```
[2024-05-27T19:00:04.627604+00:00] report.ERROR: Cron Job indexer_clean_all_changelogs has an error: Table catalog_data_exporter_products_cl does not exist. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":305135616,"emalloc_start":283210384} [] [] 
```

## 原因

由于[!DNL Commerce Data Export] [版本103.3.0](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes#release-9)发行版中的信息源表、索引和更改日志表中的名称更改，使用[!DNL Commerce Data Export]扩展名的自定义扩展中的[!DNL Mview]订阅可能无法正常工作。

在这种情况下，出现&#x200B;*表不存在*&#x200B;错误，因为`catalog_data_exporter`表名称已更改为`cde_products_feed`，并且您的自定义代码引用了[!DNL Data Exporter Mview]订阅中的旧名称。

## 解决方案

在自定义扩展中，编辑[!DNL Mview]配置文件(```./etc/mview.xml```)以将`catalog_data_exporter_products`表名更改为&#x200B;*`cde_products_feed`*。

以下示例显示了用于指定[!DNL Mview]订阅所跟踪的表的代码：

```
<view id="cde_products_feed" class="Magento\CatalogDataExporter\Model\Indexer\ProductFeedIndexer" group="indexer">
     <subscriptions>
         <table name="custom_table" entity_column="product_id" />
     </subscriptions>
</view>
```

## 相关阅读

Adobe Commerce Data Export Guide for [!DNL SaaS]服务中的[[!DNL SaaS] 数据导出扩展发行说明](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes)。
