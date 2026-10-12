---
title: '[!DNL Live Search]个Facet未按字母顺序排序'
description: 如果[!DNL Live Search]方面未按字母顺序排序，本文将提供故障诊断信息。
feature: Admin Workspace, Categories, Search
role: Developer
exl-id: 59f86727-c2a6-4418-8753-40f7937e059c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%
---
# [!DNL Live Search]个Facet未按字母顺序排序

## 受影响的产品和版本

Adobe Commerce版本2.4.x及更高版本

## 问题

所有Adobe Commerce店面小平面都使用单选选项按字母顺序排序，而不管分配给相应属性的输入类型如何。

## 解决方法

但是，在某些边缘情况下，Facet可能无法按照[[!DNL Live Search] Faceting工作区](https://experienceleague.adobe.com/zh-hans/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace)中的设置进行字母排序。

作为解决方法，您可以在[!UICONTROL Admin]属性部分中对产品属性进行排序。

1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;侧边栏上，转到&#x200B;**商店** > *属性* > **产品**。
1. 从表中选择属性。

   ![属性列表](assets/attribute-list.png)

1. 打开具有要排序的值的属性，然后选择&#x200B;**属性信息** > **属性**。
1. 在&#x200B;**管理选项**&#x200B;下，您可以对属性值排序。

   ![排序属性](assets/sort-attributes.png)
