---
title: Adobe Commerce 2.4.0安装因存储缓存过期而失败
description: “本文为Adobe Commerce 2.4.0安装失败并显示错误消息的问题提供了解决方案： *未定义默认网站。 请设置网站并重试。*显示在控制台中。”
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 2bba3af8919e1db8482764b8d688f95e606c2683
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Adobe Commerce 2.4.0安装因存储缓存过期而失败

本文为Adobe Commerce 2.4.0安装失败并显示错误消息的问题提供了解决方案： *未定义默认网站。 请设置网站并重试。* 显示在控制台中。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 问题

<u>先决条件：</u>
在CLI命令中依赖于Store模块API的第三方扩展是在中根据需要配置的 `composer.json`. 这会导致Adobe Commerce 2.4.0安装失败，并出现错误消息： *未定义默认网站。 请设置网站并重试。* 显示在控制台中。

## 原因

对于在CLI命令中对存储具有依赖关系的第三方扩展，将出现问题。 一个是AmazonSales Channel。

## 解决方案

在安装Adobe Commerce 2.4.0之前，商家必须：

1. 从删除这些第三方扩展 `composer.json`.
1. 安装不带扩展的Adobe Commerce。
1. 安装后添加扩展。

此问题将在2.4.1版本的范围内修复。

## 我们的支持知识库中的相关读物：

* [Adobe Commerce 2.4.0已知问题：Klarna缺少“退款”标签](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0已知问题：管理员的“创建新订单”页面上缺少两个按钮](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0、2.4.1：启用BraintreeVenmo部分发票发放](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知问题：启用了Amazon Pay，在使用返回标准结帐时缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0已知问题：在多送货结帐中删除奖励点时出现404错误](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0中的配送标签创建已知问题](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题 — 出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
