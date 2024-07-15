---
title: MySQL和Elasticsearch显示不同的结果
description: 本文为云基础架构2.2.3上的已知Adobe Commerce问题提供了一个修补程序，该问题与使用MySQL和Elasticsearch获取同一搜索查询的不同搜索结果相关。
exl-id: 37a0164a-0237-4200-ab9c-e0dbad7e2062
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MySQL和Elasticsearch显示不同的结果

>[!WARNING]
>
> 将在Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)中删除[MySQL目录搜索引擎。 在安装版本2.4.0之前，必须设置和配置Elasticsearch主机。请参阅我们的开发人员文档中的[安装和配置Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)。

本文为云基础架构2.2.3上的已知Adobe Commerce问题提供了一个修补程序，该问题与使用MySQL和Elasticsearch获取同一搜索查询的不同搜索结果相关。

## 问题：

根据所使用的搜索引擎、MySQL或Elasticsearch，使用同一筛选器集的目录搜索结果会有所不同。

<u>重现问题的步骤</u> ：

1. 安装和配置Elasticsearch。
1. 在店面，选择一个过滤器。
1. 记下匹配产品的数量。
1. 配置默认[MySQL搜索](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)。
1. 在店面，选择一个过滤器。
1. 记下匹配产品的数量。

<u>预期的结果</u>：
匹配产品的数量相同。

<u>实际结果</u>：
匹配产品的数量不同。

## Patch

修补程序已附加到本文。 要下载补丁程序，请向下滚动到文章末尾，然后单击所需的文件名，或单击以下链接：

[下载MDVA-12312\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-12312_EE_2.2.3_COMPOSER_v1.patch.zip)

[下载MDVA-14172\_EE\_2.2.6\_COMPOSER\_v1.patch](assets/MDVA-14172_EE_2.2.6_COMPOSER_v1.patch.zip)

### 兼容的Adobe Commerce版本：

修补程序是为以下对象创建的：

* 云基础架构2.2.3上的Adobe Commerce（`MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`文件）
* 云基础架构2.2.6上的Adobe Commerce（`MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`文件）

`MDVA-12312_EE_2.2.3_COMPOSER_v1.patch`修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.2.4
* 云基础架构上的Adobe Commerce 2.2.5
* Adobe Commerce内部部署2.2.3
* Adobe Commerce内部部署2.2.4
* Adobe Commerce内部部署2.2.5

`MDVA-14172_EE_2.2.6_COMPOSER_v1.patch`修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署2.2.6

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
