---
title: '当搜索引擎设置为 [!DNL Opensearch]时回退到 [!DNL Elasticsearch7] '
description: 本文提供了当Adobe Commerce中的*回退到 [!DNL Elasticsearch7]* error occurs when the search engine is set to [!DNL OpenSearch] 时问题的解决方案。
feature: Search
role: Developer
exl-id: 965d2929-5cf0-4e0a-9eed-6a656daaa120
source-git-commit: d17af0f8f92726aa5a6914fc9e1ff13268256d04
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# 当搜索引擎设置为[!DNL Opensearch]时回退到[!DNL Elasticsearch7]

本文为在Adobe Commerce中将搜索引擎设置为[!DNL OpenSearch]时出现&#x200B;*回退到[!DNL Elasticsearch7]*&#x200B;错误的问题提供了解决方案。

## 受影响的版本

云基础架构上的Adobe Commerce
2.4.4 - 2.4.4-p12
2.4.5 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch]可用作从Adobe Commerce 2.4.6、2.4.5-p12、2.4.4-p13开始的搜索引擎。

## 问题

您将&#x200B;**搜索引擎**&#x200B;设置为&#x200B;**[!DNL OpenSearch]**，但在`var/log/support_report.log`文件中看到以下类型的错误：

```[2024-04-04T00:27:41.212916+00:00] report.ERROR: opensearch search engine doesn't exist. Falling back to elasticsearch7 [] []```

<u>重现步骤</u>：

1. 通过运行此命令验证是否已安装[!DNL OpenSearch]： `curl 127.0.0.1:9200`<br>
如果它指示*1.2.4*，则表示已安装[!DNL OpenSearch]。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**。
1. 检查搜索引擎。 它将显示[!DNL Elasticsearch7]。

## 原因

即使您的版本不支持[!DNL OpenSearch]，应用程序也将只识别/接受[!DNL Elasticsearch7]作为搜索引擎。

从Adobe Commerce版本2.4.6开始，已更新应用程序，以允许选择[!DNL OpenSearch]作为搜索引擎。
如果您在非云环境中转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**，您将能够更改此选项，如下面的&#x200B;**解决方案**&#x200B;中所示。
（注意：在云环境中，此字段无法更改，因为搜索引擎在`app/etc/env.php`文件中被锁定。）

## 解决方案

更新`.magento.env.yaml`文件中的`SEARCH_CONFIGURATION`变量，并确保&#x200B;**搜索引擎**&#x200B;设置为&#x200B;*[!DNL elasticsearch7]*。

## 相关阅读

在《云基础架构上的Commerce》指南中[设置OpenSearch服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html)。
