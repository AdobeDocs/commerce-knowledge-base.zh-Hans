---
title: 我是否可以为共享目录中的价格计划内容暂存更新？
description: Adobe Commerce不提供为共享目录中的一个或多个产品计划价格更新([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=zh-Hans))的功能。
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%
---
# 我是否可以为共享目录中的价格计划内容暂存更新？

Adobe Commerce不提供为共享目录中的一个或多个产品计划价格更新([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html?lang=zh-Hans))的功能。

这意味着您不能直接从Commerce管理面板的&#x200B;**设置定价和结构**&#x200B;菜单计划此类价格更新（此菜单中没有&#x200B;**计划新更新**&#x200B;按钮）。

但是，您可以使用替代方法并计划以下项目的价格更新：

* 客户组
* 产品的基本价格

## 客户组的计划价格更新

1. 开始[计划新产品更新](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=zh-Hans)。
1. 向下滚动到&#x200B;**价格**&#x200B;字段，然后单击&#x200B;**高级定价**。

   ![advanced_pricing.png](assets/advanced_pricing.png){width="600"}

1. 在&#x200B;**客户组价格部分**&#x200B;中，选择所需的客户组并设置更新的价格。

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. 照常完成更新计划。

在此工作流中，您只能更新单个产品的价格；批量价格更新不可用。

请记住：共享目录利用客户组定价。

**相关文档**

* 在我们的用户指南中[计划更新（内容暂存）](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html?lang=zh-Hans)。
* 我们用户指南中的[高级定价](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=zh-Hans)。

## 基准价格的计划价格更新

请参阅相关文章：[基本价格更改如何影响共享目录价格？](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) 在我们的支持知识库中。
