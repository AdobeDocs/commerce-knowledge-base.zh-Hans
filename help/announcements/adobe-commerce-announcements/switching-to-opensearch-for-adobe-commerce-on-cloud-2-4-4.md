---
title: 在Cloud 2.4.4上切换到OpenSearch for Adobe Commerce
promoted: true
description: 云基础架构2.4.4上的Adobe Commerce不支持7.10之后的Elasticsearch版本。 **您必须先升级到Adobe Commerce 2.4.4，然后立即从Elasticsearch切换到OpenSearch 1.2.x。**Adobe将提供更接近Adobe Commerce 2.4.4 GA版本的详细说明。
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# 在Cloud 2.4.4上切换到OpenSearch for Adobe Commerce

云基础架构2.4.4上的Adobe Commerce不支持7.10之后的Elasticsearch版本。**您必须先升级到Adobe Commerce 2.4.4，然后立即从Elasticsearch切换到OpenSearch 1.2.x。** Adobe将提供更接近Adobe Commerce 2.4.4 GA版本的详细说明。

>[!NOTE]
>
>无论云提供商如何，都应进行切换。

Adobe Commerce内部部署在2022年3月的所有修补程序版本（2.4.4、2.4.3-p2和2.3.7-p3）中添加了对Elasticsearch7.16和OpenSearch 1.2的支持。 在2.4.4中，云基础架构上的Adobe Commerce将迁移至OpenSearch作为默认搜索引擎，因此商家在升级到Adobe Commerce 2.4.4或更高版本之前必须使用OpenSearch代替Elasticsearch。 具有Adobe Commerce本地部署的商家可以使用Elasticsearch或OpenSearch，因为Adobe Commerce将继续支持这两者。


## 什么是OpenSearch？

OpenSearch是Elasticsearch和Kibana的一个分支。 它由AWS而不是Elastic.co.维护。 若要了解更多信息，请查看GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch)。

**跨版本兼容性：**

**云基础架构上的Adobe Commerce是否支持Elasticsearch7.10？**

**是** — 从2022年1月中旬开始，Adobe Commerce on cloud infrastructure版本2.4.3-p1、2.4.3-p2和2.3.7-p3支持Elasticsearch7.10。

对于本地Adobe Commerce，建议使用最新的7.16.x版本来减轻Log4j的影响。

## 迁移：

## 商家何时可以迁移到OpenSearch？

在Adobe Commerce 2.4.4之后。

但是，在开始升级到Adobe Commerce 2.4.4之前，商家需要使用支持Elasticsearch7.10的Adobe Commerce的当前版本，并且在开始升级到Adobe Commerce 2.4.4或OpenSearch之前至少Elasticsearch。

## 未使用2.4.4的商家(云基础架构上的Adobe Commerce和Adobe Commerce内部部署)可以执行哪些操作？ 他们是否可以升级到支持的Elasticsearch版本(7.10、7.16.1)或OpenSearch？ 它们是否必须采用最新支持的版本（如2.4.3-p1、2.3.7-p2、2.4.3-p1）？

如果它们所在的Adobe Commerce核心版本支持Elasticsearch7.10 — 则它们可以使用该版本。

请查看开发人员文档中的[系统要求](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)以了解版本兼容性。

>[!NOTE]
>
>建议尽快计划升级到Adobe Commerce 2.4.4，因为Elasticsearch7.10将于2022年5月停用。

Adobe合作伙伴可以在[此处](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html)注册我们的测试版计划，以访问我们最新的Beta4代码，该代码已针对Elasticsearch7.16.1和OpenSearch 1.1进行了测试。
