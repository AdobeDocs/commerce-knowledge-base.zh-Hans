---
title: 无法使用Commerce管理更改搜索引擎（搜索引擎菜单不可访问）
description: 本文提供了一个解决方案，用于在“Adobe Commerce搜索引擎”字段未显示或“使用系统值”复选框灰显且不可访问时，使用Commerce管理员更改搜索引擎。
exl-id: 5b0f728c-6a8d-446d-9553-5abc3d01e516
feature: Admin Workspace, Search, Variables
role: Developer
source-git-commit: 0ea7bbef7fec556f9a90151be9cf1077f5cfac45
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 0%

---

# 无法使用Commerce管理更改搜索引擎（搜索引擎菜单不可访问）

>[!WARNING]
>
> 将在Adobe Commerce 2.4.0[&#128279;](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)中删除MySQL目录搜索引擎。 在安装版本2.4.0之前，必须设置并配置Elasticsearch主机。
> 
> 请参阅：
> [安装和配置Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。
> [安装和配置Opensearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)
> [安装和配置实时搜索](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install)

本文提供了一个解决方案，用于在&#x200B;**搜索引擎**&#x200B;字段未显示或&#x200B;**使用系统值**&#x200B;复选框灰显且不可访问的情况下，使用Commerce管理员更改Adobe Commerce搜索引擎。

在本文中：

* [受影响的版本](#affected-versions)
* [使用Commerce管理更改搜索引擎（步骤）](#change-search-engine-using-magento-admin-steps)
* [Adobe Commerce内部部署问题](#magento-commerce-on-premise)
* [云基础架构上的Adobe Commerce](#magento-commerce-cloud)

## 受影响的版本

* Adobe Commerce内部部署：2.4.X
* 云基础架构上的Adobe Commerce：
   * 版本：2.4.X
   * 入门和专业计划体系结构
* MySQL、Elasticsearch、Opensearch、Live Search：所有支持的版本

## 使用管理员更改搜索引擎（步骤）

1. 以管理员身份登录&#x200B;**[!UICONTROL Admin]**。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;侧栏的左侧，单击&#x200B;**[!UICONTROL Stores]**。
1. 在&#x200B;**[!UICONTROL Settings]**&#x200B;下，选择&#x200B;**[!UICONTROL Configuration]**。
1. 导航到左侧&#x200B;**[!UICONTROL Catalog]、**&#x200B;下的面板，然后选择&#x200B;**[!UICONTROL Catalog]**。
1. 展开&#x200B;**[!UICONTROL Catalog Search]**&#x200B;部分。    ![catalog_menu.png](assets/catalog_menu.png)
1. 转到&#x200B;**[!UICONTROL Search Engine]**&#x200B;字段并从&#x200B;**[!UICONTROL Use system value]**&#x200B;复选框中删除所选内容。
1. 单击&#x200B;**[!UICONTROL Search Engine]**&#x200B;菜单并选择以下所示的可用选项之一。    ![search_engine_menu.png](assets/search_engine_menu.png)
1. 单击页面右上角的&#x200B;**[!UICONTROL Save Config]**。

## Adobe Commerce内部部署问题

### 问题1：不显示搜索引擎字段

当您访问&#x200B;**目录搜索**&#x200B;部分时，**搜索引擎**&#x200B;菜单完全不显示。

![search_engine_not_displayed.png](assets/search_engine_not_displayed.png)

### 原因：存储视图不是默认配置

管理员的“商店视图”已设置为&#x200B;*默认配置*&#x200B;以外的任何值。

搜索引擎是在应用程序级别设置的全局配置，而不是在存储范围中设置的全局配置。 Adobe Commerce应用程序中的商店不能使用其他搜索引擎。

### 解决方案：将存储视图设置为默认配置

1. 以管理员身份登录&#x200B;**[!UICONTROL Admin]**。
1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;侧栏的左侧，单击&#x200B;**[!UICONTROL Stores]**。
1. 导航到&#x200B;**[!UICONTROL Settings]**&#x200B;并选择&#x200B;**[!UICONTROL Configuration]**。
1. 单击左上角的&#x200B;**[!UICONTROL Store View]**&#x200B;选择器，然后选择&#x200B;**[!UICONTROL *默认配置&#x200B;*]**。
1. 单击确认对话框中的&#x200B;**[!UICONTROL OK]**&#x200B;以批准存储视图更改。

![change_store_view.png](assets/change_store_view.png)

**相关文档：** [更改用户指南中的作用域](https://experienceleague.adobe.com/docs/commerce-admin/config/scope-change.html#set-the-scope)。

### 问题2：无法取消选中“使用系统值”

当您访问管理员的&#x200B;**目录搜索**&#x200B;部分时，**使用系统值**&#x200B;复选框呈灰显状态，因此您以后无法从复选框中删除选定内容以更改搜索引擎。

### 原因

默认搜索引擎已在`app/etc/env.php`或`app/etc/config.php`文件中的应用程序配置级别上配置，因此无法使用管理员进行更改。

具有默认搜索引擎配置的部分的示例：

```php
'system'=>
array (
'default'=>
array (
'catalog'=>
array (
'search'=>
array (
'engine'=>'mysql',
),
),
),
),
```

### 解决方案

从`app/etc/env.php`或`app/etc/config.php`配置文件中删除带有默认搜索引擎配置的部分。

### 我们的开发人员文档中的相关文章

Adobe Commerce配置指南中的[Adobe Commerce配置文件](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/files/deployment-files.html)

## 云基础架构上的Adobe Commerce

由于云基础架构的组织方式，使用管理员切换搜索引擎在Adobe Commerce上不可用。

在部署过程中，云基础架构部署脚本上的Adobe Commerce会检查是否已在`MAGENTO_CLOUD_RELATIONSHIPS`变量中声明了Elasticsearch。 如果已声明，则Elasticsearch被选为活动搜索引擎并自动配置；[MySQL搜索引擎](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)在管理员中变得不可访问。 如果未声明Elasticsearch关系，则MySQL将设置为活动，并且Elasticsearch将无法访问。

不建议直接在云环境中编辑`app/etc/env.php`或`app/etc/config.php`配置文件；这就是为什么更改这些文件以使Elasticsearch引擎显示在管理员中（我们在上一节中推荐的解决方案）不适用于您的云项目。

### 在暂存和生产环境中更改搜索引擎

在将搜索引擎从MySQL切换到暂存环境和生产环境上的Elasticsearch之前，请确保您以前已[提交了一个支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求启用环境上的Elasticsearch，并且该票证已成功解析。

要更改暂存和生产环境中使用的搜索引擎，请更改本地环境中`.magento.env.yaml`文件中的`SEARCH_CONFIGURATION`环境变量，然后将更改推送到集成和暂存/生产环境，以使更改生效。

如果您正在切换到Elasticsearch7，则生成的`.magento.env.yaml`文件中的SEARCH\_CONFIGURATION变量可能如下所示：

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

如果您正在切换到[Opensearch（在2.4.6及更高版本中）](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/search-engine-shown-elasticsearch-despite-open-search)，则生成的`.magento.env.yaml`文件中的SEARCH\_CONFIGURATION变量可能如下所示：

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: opensearch
     elasticsearch_server_hostname: hostname
     elasticsearch_server_port: '12345'
     elasticsearch_index_prefix: magento
     elasticsearch_server_timeout: '15'
```

如果您[正在切换到Live Search](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/error-opensearch-search-engine-doesnt-exist-falling-back-to-livesearch)，则生成的`.magento.env.yaml`文件中的SEARCH\_CONFIGURATION变量可能如下所示：

```yaml
stage:
  deploy:
   SEARCH_CONFIGURATION:
     engine: livesearch
```

### 相关文档

#### 支持知识库

* [在云中启用Elasticsearch](/help/how-to/general/enable-elasticsearch-on-cloud.md)

#### 开发人员文档

* [设置Elasticsearch服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch.html)
* [生成和部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) （有关`.magento.env.yaml`配置文件的文档）
* [部署变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html) （[SEARCH\_CONFIGURATION节](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#search_configuration)）
* [服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) （有关`.magento/services.yaml`配置文件的文档）
* [实时搜索](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)
