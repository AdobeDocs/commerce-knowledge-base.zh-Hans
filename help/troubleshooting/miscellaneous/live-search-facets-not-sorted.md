---
title: “[!DNL Live Search] Facet未按字母顺序排序”
description: 如果 [!DNL Live Search] 方面未按字母顺序排序，本文将提供故障诊断信息。
feature: Admin Workspace, Categories, Search
role: Developer
source-git-commit: 5387edb46281fc536402f8ce0a5e2a77c1bd4193
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# [!DNL Live Search]个Facet未按字母顺序排序

## 受影响的产品和版本

Adobe Commerce版本2.4.x及更高版本

所有Adobe Commerce店面小平面都使用单选选项按字母顺序排序，而不管分配给相应属性的输入类型如何。

但是，在某些边缘情况下，Facet可能无法按照[[!DNL Live Search] Faceting工作区](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/facets/faceting-workspace)中的设置进行字母排序。 作为解决方法，您可以在[!UICONTROL Admin]属性部分中对产品属性进行排序。

1. 在&#x200B;**[!UICONTROL Admin]**&#x200B;侧边栏上，转到&#x200B;**商店** > *属性* > **产品**。
1. 从表中选择属性。

   ![属性列表](assets/attribute-list.png)

1. 打开具有要排序的值的属性，然后选择&#x200B;**属性信息** > **属性**。
1. 在&#x200B;**管理选项**&#x200B;下，您可以对属性值排序。

   ![排序属性](assets/sort-attributes.png)
