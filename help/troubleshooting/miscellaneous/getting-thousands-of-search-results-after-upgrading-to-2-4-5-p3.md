---
title: 在寻找特定产品时获得数千个结果
description: 本文提供了一种解决方案，来解决您在查找特定产品时会获得数千个搜索结果的问题。
feature: Quotes, Search, Returns
role: Developer, Admin
exl-id: 0eccf212-96be-4ea5-9e6e-95f27d7d9f92
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '190'
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
