---
title: Adobe Commerce 2.4.0：Braintree不在多个地址中签出
description: 本文为Adobe Commerce 2.4.0的已知问题提供了解决方法，该问题导致在多个地址结账时未使用Braintree支付方法。 请注意，Adobe Commerce 2.4.1中已修复此问题。
exl-id: efde0bba-fd4a-490b-becb-856cb9ea58a5
feature: Checkout, Compliance, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：Braintree不在多个地址中签出

本文为Adobe Commerce 2.4.0的已知问题提供了解决方法，该问题导致在多个地址结账时未使用Braintree支付方法。 请注意，Adobe Commerce 2.4.1中已修复此问题。

注意：Adobe Commerce建议对版本2.3及更高版本使用[Commerce Marketplace Braintree扩展](https://marketplace.magento.com/paypal-module-braintree.html)，以保持PSD合规性。 该扩展不提供多地址签出功能。

## 受影响的产品和版本

* Adobe Commerce内部部署v2.4.0
* 云基础架构上的Adobe Commerce v2.4.0

## 问题

<u>先决条件</u>：

使用核心Braintree集成。

<u>重现步骤</u>：

1. 去店面。
1. 以客户身份登录。
1. 将产品添加到购物车。
1. 打开购物车。
1. 按&#x200B;**查看和编辑购物车**。
1. 按&#x200B;**签出多个地址**。
1. 按&#x200B;**转到送货信息**。
1. 按&#x200B;**继续记帐信息**。

<u>预期的结果</u>：

Braintree可用作支付方式。

<u>实际结果</u>：

Braintree不可用作支付方式。

## 解决方法

如果使用Adobe Commerce 2.4.0中的Braintree，请勿启用多地址选项。已在Adobe Commerce 2.4.1中修复此问题。

## 我们的支持知识库中的相关阅读

* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题 — 出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
