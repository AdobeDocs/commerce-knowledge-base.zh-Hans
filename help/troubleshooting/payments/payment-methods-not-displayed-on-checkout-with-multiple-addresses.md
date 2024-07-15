---
title: 使用多个地址结账时未显示支付方式
description: 本文解释了在指定多个运送地址时，大多数付款方法不会在结账时显示，因为此功能仅针对Cybersource实施。
exl-id: 68a9ee77-d0ef-43c5-9667-6d099b797666
feature: Checkout, Orders, Payments, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# 使用多个地址结账时未显示支付方式

本文解释了在指定多个运送地址时，大多数付款方法不会在结账时显示，因为此功能仅针对Cybersource实施。

## 受影响的产品和版本

* Adobe Commerce内部部署2.x.x
* 云基础架构上的Adobe Commerce 2.x.x

>[!NOTE]
>
>核心的Adobe Commerce网络源支付集成自2.3.3之后已被弃用，并将在2.4.0中完全删除。请改用Marketplace中的[正式扩展](https://marketplace.magento.com/cybersource-global-payment-management.html)。

## 问题

<u>先决条件</u>：在Commerce管理员中，启用并配置PayPal和Cybersource支付方式，并为您的商店启用多送货服务。

<u>重现步骤</u>：

1. 在店面，将多个产品添加到购物车。
1. 转到购物车页面。
1. 单击&#x200B;**签出多个地址**。
1. 登录或创建帐户。
1. 在“收货地址 — 多个地址”页上的地址之间拆分产品。
1. 单击&#x200B;**转到送货信息**。
1. 选择每个装运的装运方法。
1. 单击&#x200B;**继续查看帐单信息**。

<u>预期结果</u>： PayPal和Cybersource可作为付款选项使用。

<u>实际结果</u>：只有赛博源显示为可用支付选项。

## 原因

目前，从2.2.4版开始，Cybersource是多邮寄结账唯一支持的实时支付方法。可能会为每个支付方式逐个构建对多种配送的支持。 目前无法提供确切日期或发行版本号。
