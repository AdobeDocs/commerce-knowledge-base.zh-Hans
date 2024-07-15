---
title: 'MDVA-40101：下单后商品仍为迷你购物车PayPal Express结帐'
description: MDVA-40101修补程序修复了在使用PayPal Express结帐成功下订单后无法从微型购物车中删除项目的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-40101。 请注意，Adobe Commerce 2.4.0中已修复此问题。
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101：下单后商品仍为迷你购物车PayPal Express结帐

MDVA-40101修补程序修复了在使用PayPal Express结帐成功下订单后无法从微型购物车中删除项目的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-40101。 请注意，Adobe Commerce 2.4.0中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.3.7

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使使用PayPal Express结帐成功下订单，商品仍会保留在迷你购物车中。

<u>重现步骤</u>：

在浏览器中，以无痕模式使用PayPal Express Checkout下订单。

<u>预期的结果</u>：

成功完成订单后，迷你购物车应为空。

<u>实际结果</u>：

* 成功页面显示一个空的迷你购物车。
* 所有其他页面显示包含已购项目的迷你购物车。
* 单击购物车链接会将您重定向到空的购物车页面。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
