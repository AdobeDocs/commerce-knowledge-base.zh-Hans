---
title: 'MDVA-36138：免费送货规则未应用购物车多个项目'
description: MDVA-36138修补程序修复了当购物车中有多个项目时，免费配送中匹配的SKU无法免费配送的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21后，即可使用此修补程序。 修补程序ID为MDVA-36138。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: 74e25ca8-e4fa-47f4-ab95-561f70e05727
feature: Orders, Shipping/Delivery, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# MDVA-36138：免费送货规则未应用购物车多个项目

MDVA-36138修补程序修复了当购物车中有多个项目时，免费配送中匹配的SKU无法免费配送的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21时，此修补程序可用。 修补程序ID为MDVA-36138。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.4

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.2及更高版本

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果免运费规则仅应用于特定项目，则当购物车中有其他项目时，折扣不适用。

<u>重现步骤</u>：

1. 创建简单产品 — simple1和simple2。
1. 配置USPS（或任何联机配送方式）：

   * 允许的方法：优先级邮件（选择一种方法，目的是在购物车和结账时不会出现方法长列表）。
   * 空闲方法：优先级邮件。

1. 创建购物车规则：

   * 指定优惠券代码
   * “条件”选项卡：留空
   * “操作”选项卡：

   `Condition: SKU is simple1`
   `Free Shipping: For matching items only`

1. 将simple1添加到购物车。
1. 应用优惠券代码。
1. 将simple2添加到购物车。

<u>预期的结果</u>：

* simple1 — 应提供免费送货。
* simple2 — 应支付运费。

<u>实际结果</u>：

运费包括simple1和simple2。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
