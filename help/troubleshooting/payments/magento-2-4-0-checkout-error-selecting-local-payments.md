---
title: Adobe Commerce 2.4.0：选择本地付款时出现结账错误
description: 本文介绍了结账过程中Adobe Commerce中一个已知问题的解决方案，该问题导致在某些国家/地区选择本地支付方式时出现错误消息。 这种情况发生在以下国家：比利时、意大利、荷兰、波兰和西班牙。
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%
---
# Adobe Commerce 2.4.0：选择本地付款时出现结账错误

本文介绍了结账过程中Adobe Commerce中一个已知问题的解决方案，该问题导致在某些国家/地区选择本地支付方式时出现错误消息。 这种情况发生在以下国家：比利时、意大利、荷兰、波兰和西班牙。

错误消息&#39;&#39;*&#39;目前没有可用的付款方式。 请更新您的帐单地址。* 将会出现，但本地支付方式仍会出现并正常运行。 Adobe Commerce 2.4.1中将提供永久修复。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>先决条件</u>：

* 已安装Adobe Commerce 2.4.0。
* 创建一个产品和一个类别。
* 配置[Braintree付款方式](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree/)。

<u>重现步骤</u>：

1. 导航到店面。
1. 选择要添加到购物车的项目。
1. 继续结帐。
1. 使用有效地址填写地址表。
1. 进入Review &amp; Payments页面。

<u>预期的结果</u>：

本地支付方式应正常显示，且不会显示错误消息。

<u>实际结果</u>：

错误消息&#39;&#39;*&#39;目前没有可用的付款方式。 请更新您的帐单地址。* 显示，但本地支付方式仍会显示并正常运行。

## 解决方案

解决方法是忽略显示的错误消息并继续正常付款，因为所有本地付款方法都将正常运行。 从Adobe Commerce版本2.4.1开始，提供了此修补程序。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：Braintree支付方法未出现在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
