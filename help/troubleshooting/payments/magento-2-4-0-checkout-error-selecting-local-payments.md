---
title: 'Adobe Commerce 2.4.0：选择本地付款时出现结账错误'
description: “本文介绍了结账期间Adobe Commerce中一个已知问题的解决方案，该问题导致在某些国家/地区选择本地支付方式时出现错误消息。 这种情况发生在比利时、意大利、荷兰、波兰和西班牙等国家。
exl-id: de2eafb0-d03c-4ff8-9615-0f2676d95848
feature: B2B, Categories, Checkout, Orders, Payments
role: Developer
source-git-commit: a8cc7ad0cb9cb111f5b9636ff18aef3b6ed44329
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：选择本地付款时出现结账错误

本文介绍了结账过程中Adobe Commerce中一个已知问题的解决方案，该问题导致在某些国家/地区选择本地支付方式时出现错误消息。 这种情况发生在以下国家：比利时、意大利、荷兰、波兰和西班牙。

错误消息&#39;&#39;*&#39;目前没有可用的付款方式。 请更新您的帐单地址。“*”将会出现，但本地付款方式仍会出现，并且工作正常。 Adobe Commerce 2.4.1中将提供永久修复。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>先决条件</u>：

* 已安装Adobe Commerce 2.4.0。
* 创建一个产品和一个类别。
* 配置[Braintree付款方式](https://developer.adobe.com/commerce/webapi/graphql/payment-methods/braintree.html)。

<u>重现步骤</u>：

1. 导航到店面。
1. 选择要添加到购物车的项目。
1. 继续结帐。
1. 使用有效地址填写地址表。
1. 进入Review &amp; Payments页面。

<u>预期的结果</u>：

本地支付方式应正常显示，且不会显示错误消息。

<u>实际结果</u>：

错误消息&#39;&#39;*&#39;目前没有可用的付款方式。 请更新您的帐单地址。“*”出现，但本地付款方式仍会显示并正常工作。

## 解决方案

解决方法是忽略显示的错误消息并继续正常付款，因为所有本地付款方法都将正常运行。 从Adobe Commerce版本2.4.1开始，提供了此修补程序。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题：无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
