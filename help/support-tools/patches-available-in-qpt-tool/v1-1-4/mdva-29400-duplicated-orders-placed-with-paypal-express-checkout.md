---
title: 'MDVA-29400：使用PayPal Express结帐下达的订单重复'
description: MDVA-29400修补程序解决了客户通过PayPal Express结帐下订单时创建重复订单的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-29400。 请注意，Adobe Commerce 2.4.1中已修复此问题。
exl-id: 75b943c8-5f7c-4d94-ae92-935428fdfcf8
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-29400：使用PayPal Express结帐下达的订单重复

MDVA-29400修补程序解决了客户通过PayPal Express结帐下订单时创建重复订单的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-29400。 请注意，Adobe Commerce 2.4.1中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.3.7-p1， 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户使用PayPal Express结帐下订单时，将会创建重复的订单。

<u>先决条件</u>：

已启用并配置了PayPal Express签出。

<u>重现步骤</u>：

1. 将产品添加到购物车。
1. 转到“结帐”页面并使用PayPal Express作为付款方式。
1. 它将重定向到paypal/express/review/页面。
1. 下单。 您将被重定向到成功页面。
1. 返回PayPal/express/review/页面。
1. 单击&#x200B;**下订单**&#x200B;按钮。

<u>预期的结果</u>：

仅创建一个订单。

<u>实际结果</u>：

您收到以下错误：*PayPal Express签出令牌不存在*，但已成功下第二张订单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
