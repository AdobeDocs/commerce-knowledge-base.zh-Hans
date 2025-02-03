---
title: 实时搜索目录未同步
description: 本文为使用Live Search扩展时目录数据无法正确同步的Adobe Commerce问题提供了解决方案。
exl-id: cd2e602f-b2c7-4ecf-874f-ec5f99ae1900
feature: Catalog Management, Search
role: Developer
source-git-commit: 96e5bfc677949fb5f925040b95f951ca518fa71a
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# 实时搜索目录未同步

本文为使用Live Search扩展时目录数据无法正确同步的Adobe Commerce问题提供了解决方案。

## 受影响的产品和版本

* 已安装Live Search扩展的Adobe Commerce 2.4.x

## 问题

您的目录数据未正确同步，或者已添加新产品，但未显示在搜索结果中。 您还可能会在`var/log/exception.log`中收到以下错误：

`Magento_LiveSearch: An error occurred in search backend. {"result":{"errors":[{"message":"Exception while fetching data (/productSearch) : No index was found for this request"}]}}`

>[!NOTE]
>
>从[!DNL Live Search]版本4.2.1开始，表名`catalog_data_exporter_products`和`catalog_data_exporter_product_attributes`现在称为`cde_products_feed`和`cde_product_attributes_feed`。对于版本低于4.2.1的商家，在旧表名称`catalog_data_exporter_products`和`catalog_data_exporter_product_attributes`中查找数据。

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

1. 使用以下[!DNL SQL]查询并验证您是否在`feed_data`列中有所需数据。 另外，记下`modified_at`时间戳。

   ```sql
   select * from cde_products_feed where sku = '<your_sku>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果看不到正确的数据，请尝试使用以下命令重新编入索引，并在步骤1中重新运行[!DNL SQL]查询以验证数据：

   ```bash
   bin/magento indexer:reindex cde_products_feed
   ```

1. 如果仍看不到正确的数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 检查上次产品导出的时间戳

1. 如果您在`cde_products_feed`中看到正确的数据，请使用以下[!DNL SQL]查询检查上次导出的时间戳。 它应在`modified_at`时间戳之后：

   ```sql
   select * from scopes_website_data_exporter;
   ```

1. 如果时间戳较旧，则可以等待下一个cron运行，也可以使用以下命令自行触发该时间戳：

   ```bash
   bin/magento cron:run --group=saas_data_exporter
   ```

1. 等待`<>`时间（增量更新的时间）。 如果您仍未看到数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 同步特定的属性代码

如果特定属性代码的产品属性数据未正确同步，请执行以下操作：

1. 使用以下[!DNL SQL]查询并验证您是否在`feed_data`列中有所需数据。 另外，记下`modified_at`时间戳。

   ```sql
   select * from cde_product_attributes_feed where json_extract(feed_data, '$.attributeCode') = '<your_attribute_code>' and store_view_code = '<your_ store_view_code>';
   ```

1. 如果看不到正确的数据，请使用以下命令重新编制索引，然后在步骤1中重新运行[!DNL SQL]查询以验证数据。

   ```bash
   bin/magento indexer:reindex cde_product_attributes_feed
   ```

1. 如果仍看不到正确的数据，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 检查上次产品属性导出的时间戳

如果您在`cde_product_attributes_feed`中看到了正确的数据：

1. 使用以下[!DNL SQL]查询检查上次导出的时间戳。 它应在`modified_at`时间戳之后。

   ```sql
   select * from scopes_website_data_exporter;
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

运行以下命令以重新同步馈送：

```
bin/magento saas:resync --feed productattributes --cleaup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productOverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```

[提交支持请求](https://experienceleague.adobe.com/home?support-tab=home#support)以请求重新索引实时搜索索引。 在问题描述中，包括在&#x200B;**[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Commerce Services Connector]**&#x200B;下的管理面板中找到的数据空间/环境ID。

## 相关阅读

* 在我们的用户文档中[载入Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/onboarding-overview.html)
* [在Adobe Commerce SaaS Data Export Guide中查看日志并排除Adobe Commerce SaaS数据导出和同步问题](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
