---
title: 尽管安装了 [!DNL OpenSearch] ，[!DNL Elasticsearch]仍显示为搜索引擎
description: 本文针对 [!DNL Elasticsearch] 在安装或升级到 [!DNL OpenSearch]后仍显示为云上Adobe Commerce的搜索引擎的问题提供了解决方案。
exl-id: cdd8a35d-da6f-46d3-b732-65626487c9bb
feature: Install
source-git-commit: b3f68e43ce3c4fdea001db1d8ba2774900db7dba
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 尽管安装了[!DNL OpenSearch]，[!DNL Elasticsearch]仍显示为搜索引擎

本文为即使在安装或升级到[!DNL OpenSearch]后，[!DNL Elasticsearch]仍显示为云上Adobe Commerce的搜索引擎的问题提供了解决方案。

## 受影响的版本

Adobe Commerce on cloud 2.4.4 - 2.4.5-p11

>[!NOTE]
>
>[!DNL OpenSearch]可用作从Adobe Commerce 2.4.6开始的搜索引擎。

## 问题

即使在安装或升级到[!DNL OpenSearch]后，[!DNL Elasticsearch]仍显示为Adobe Commerce云中的搜索引擎。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**。
1. 检查搜索引擎。 它将显示[!DNL Elasticsearch7]。

## 原因

[!DNL Elasticsearch7]在Adobe Commerce中硬编码为这些版本中使用的搜索引擎。

请不要将其与安装的服务版本混淆。 即使代码中未包含[!DNL Opensearch]模块，Adobe Commerce仍能够使用基础[!DNL Opensearch]服务。

## 解决方案

要验证是否已安装[!DNL OpenSearch]，请运行以下命令：

**方法1**：

* 在服务器上运行以下命令： `curl 127.0.0.1:9200`。 它应返回[!DNL OpenSearch]及其版本。

示例：

```
$ curl 127.0.0.1:9200
{
  "name" : $clusterName,
  "cluster_name" : "opensearch_stg",
  "cluster_uuid" : $clusterUuid,
  "version" : {
    "distribution" : "opensearch",
    "number" : "1.2.4",
    "build_type" : "deb",
    "build_hash" : "44ccdbaed5fe5a8b02d99a611857a671b6dd909d",
    "build_date" : "2022-11-08T09:23:45.993372Z",
    "build_snapshot" : false,
    "lucene_version" : "8.10.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

**方法2**：

* 在Magento-cloud CLI上使用以下命令： `magento-cloud relationships -p <project_id>`。 使用该命令后，找到[!DNL OpenSearch]。

## 相关阅读

在《云基础架构上的Commerce》指南中[设置OpenSearch服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/opensearch.html)。
