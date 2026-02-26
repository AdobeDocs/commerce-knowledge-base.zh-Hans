---
title: Adobe Commerce 2.4.0安装因存储缓存过期而失败
description: 本文为Adobe Commerce 2.4.0安装失败并出现以下错误消息的问题提供了解决方案： *未定义默认网站。 请设置网站并重试。*显示在控制台中。
exl-id: 0680199b-7e47-4a8c-91fe-9f6c32839a0e
feature: B2B, Cache, Console, Install, Upgrade
role: Developer
source-git-commit: 7705b6030d2f0877c228dae1707916ad38c9d587
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Adobe Commerce 2.4.0安装因存储缓存过期而失败

本文为Adobe Commerce 2.4.0安装失败并出现以下错误消息的问题提供了解决方案： *未定义默认网站。 请设置网站并重试。*&#x200B;显示在控制台中。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 问题

<u>先决条件：</u>
在`composer.json`中根据需要配置了在CLI命令中依赖于Store模块的API的第三方扩展。 这会导致Adobe Commerce 2.4.0安装失败，并出现错误消息： *未定义默认网站。 请设置网站并重试。*&#x200B;显示在控制台中。

## 原因

对于在CLI命令中对存储具有依赖关系的第三方扩展，将出现问题。 一个是Amazon Sales Channels。

## 解决方案

在安装Adobe Commerce 2.4.0之前，商家必须：

1. 从`composer.json`中删除这些第三方扩展。
1. 安装不带扩展的Adobe Commerce。
1. 安装后添加扩展。

此问题将在2.4.1版本的范围内修复。

## 我们的支持知识库中的相关读物：

* [Adobe Commerce 2.4.0已知问题：Klarna缺少“退款”标签](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0、2.4.1：启用Braintree Venmo部分发票发放](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知问题：启用了Amazon Pay，在使用返回标准结帐时缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方法未出现在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)

