---
title: 'MDVA-31363修补程序：购物车价格规则不适用(GraphQL)'
description: MDVA-31363修补程序修复了在使用“整个购物车的固定金额折扣”操作时，带有优惠券的购物车价格规则不通过GraphQL应用的问题。 安装Quality Patches Tool (QPT) 1.0.9后，即可使用此修补程序。 此问题计划在Adobe Commerce版本2.4.2中修复。
exl-id: f64fbbb1-b5fd-4624-bcdd-d1e6c1f9acfe
feature: GraphQL, Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-31363修补程序：购物车价格规则不适用(GraphQL)

>[!WARNING]
>
>名为MDVA-33975的新修补程序修复了GraphQL的价格计算问题。 MDVA-31363已弃用，建议您应用修补程序MDVA-33975。 要访问此修补程序，请参阅[MDVA-33975修补程序：GraphQL价格计算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html)。

MDVA-31363修补程序修复了在使用“整个购物车的固定金额折扣”操作时，带有优惠券的购物车价格规则不通过GraphQL应用的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9时，此修补程序可用。 此问题计划在Adobe Commerce版本2.4.2中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.2 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在就报价价格作出回应之前重新计算报价总额会导致应用的规则丢失。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 为整个购物车创建具有固定金额折扣的购物车价格规则。
1. 使用GraphQL创建新的购物车。
1. 保存响应中的card\_id ，并使用GraphQL将步骤1中的产品添加到购物车。
1. 通过使用GraphQL将优惠券代码添加到购物车来激活购物车价格规则。
1. 检查价格以响应。

<u>预期的结果</u>：

应用折扣。

<u>实际结果</u>：

不应用折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
