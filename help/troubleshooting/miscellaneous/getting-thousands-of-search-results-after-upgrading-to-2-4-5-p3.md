---
title: 在寻找特定产品时获得数千个结果
description: 本文提供了一种解决方案，来解决您在查找特定产品时会获得数千个搜索结果的问题。
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 在寻找特定产品时获得数千个结果

本文提供了一种解决方案，来解决您在查找特定产品时会获得数千个搜索结果的问题。

## 受影响的产品和版本

* 已安装[!DNL ElasticSearch]的Adobe Commerce所有版本

## 问题

您正在查找特定产品（例如，*WSH12-32-Red*），但搜索返回了大量类似的产品。

## 解决方案

[!DNL ElasticSearch]中全文搜索的性质基于相关性，而不是完全匹配。 因此，首先排序的是大多数相关的匹配项（如完全匹配的SKU）。

但是，如果您需要与搜索词完全匹配的搜索结果（完全匹配），则应该在搜索查询中使用引号。 例如，查询不带引号的&#x200B;*WSH12-32-Red*&#x200B;将返回多个结果，结果中首先出现的是完全匹配的结果（具有&#x200B;*SKU WSH12-32-Red*&#x200B;的产品）。 但是，引用查询&#x200B;*&quot;WSH12-32-Red&quot;*&#x200B;将只返回一个完全匹配的结果。
