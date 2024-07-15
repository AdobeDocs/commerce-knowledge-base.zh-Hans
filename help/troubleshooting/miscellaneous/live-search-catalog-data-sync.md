---
title: 实时搜索目录未同步
description: 本文为使用Live Search扩展时目录数据无法正确同步的Adobe Commerce问题提供了解决方案。
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: a1b049dab989d5d8594d86b64b778e6e277a9f41
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---

# 实时搜索目录未同步

本文为使用Live Search扩展时目录数据无法正确同步的Adobe Commerce问题提供了解决方案。

## 受影响的产品和版本

* 已安装Live Search扩展的Adobe Commerce 2.4.x

## 问题

您的目录数据未正确同步，或者添加了新产品，但未显示在搜索结果中。

<u>重现步骤</u>

1. 按照用户文档中的[安装Live Search >配置API密钥](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#configure-api-keys)中所述，为Adobe Commerce实例配置并连接Live Search。
1. 30分钟后，按照用户文档中的[安装Live Search >验证导出](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#verify-export)中的说明验证导出的目录数据。
1. 30分钟后，按照用户文档中的[安装Live Search >测试连接](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#test-connection)中的说明测试连接。

或

1. 向目录中添加新产品。
1. 尝试在运行Magento索引器+ cron后的15-20分钟后使用产品名称或其他可搜索属性运行搜索查询，以将数据同步到后端服务。

<u>预期的结果</u>

* 可以验证导出的目录数据
* 连接成功
* 新产品会显示在搜索结果中。

<u>实际结果</u>

无法验证导出的目录和/或连接未建立，因为API密钥已更改。

## 解决方案

您可以通过多种方法来尝试并修复目录同步问题。

### 等待应用更改

配置并连接后，可能需要超过30分钟才能在ES(Elasticsearch)中创建索引并返回搜索结果。 后续的一次性产品更新预计会在几分钟内编制索引。

### 同步特定SKU的产品数据

如果特定SKU的产品数据未正确同步，请执行以下操作：

1. 使用以下SQL查询并验证您是否在`feed_data`列中有所需数据。 另外，记下`modified_at`时间戳。

   ```sql
   select * from catalog_data_exporter_products where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果看不到正确的数据，请尝试使用以下命令重新编制索引，然后在步骤1中重新运行SQL查询以验证数据：

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_products
   ```

1. 如果仍看不到正确的数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 检查上次产品导出的时间戳

1. 如果您在`catalog_data_exporter_products`中看到正确的数据，请使用以下SQL查询检查上次导出的时间戳。 它应在`modified_at`时间戳之后：

   ```sql
   select * from flag where flag_code = 'products-feed-version';
   ```

1. 如果时间戳较旧，则可以等待下一个cron运行，也可以使用以下命令自行触发该时间戳：

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 等待`<>`时间（增量更新的时间）。 如果您仍未看到数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 同步特定的属性代码

如果特定属性代码的产品属性数据未正确同步，请执行以下操作：

1. 使用以下SQL查询并验证您是否在`feed_data`列中有所需数据。 另外，记下`modified_at`时间戳。

   ```sql
   select * from catalog_data_exporter_product_attributes where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果看不到正确的数据，请使用以下命令重新编制索引，然后重新运行步骤1中的SQL查询来验证数据。

   ```bash
   bin/magento indexer:reindex catalog_data_exporter_product_attributes
   ```

1. 如果仍看不到正确的数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 检查上次产品属性导出的时间戳

如果您在`catalog_data_exporter_product_attributes`中看到了正确的数据：

1. 使用以下SQL查询检查上次导出的时间戳。 它应在`modified_at`时间戳之后。

   ```sql
   select * from flag where flag_code = 'product-attributes-feed-version';
   ```

1. 如果时间戳较旧，则可以等待下一个cron运行，也可以使用以下命令自行触发该时间戳：

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 等待15-20分钟（增量更新的时间）。 如果您仍未看到数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 在API配置更改后同步

（已知问题）如果您更改了API配置，从而导致数据空间ID发生更改，并且发现目录更改不再同步，请运行以下命令：

```bash
bin/magento saas:resync --feed products
bin/magento saas:resync --feed productattributes
```

## 相关阅读

请参阅我们的用户文档中的[载入实时搜索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html)。
