---
title: 'Adobe Commerce 2.3.5已知问题：虚拟产品多发运订单'
description: 本文说明了Adobe Commerce 2.3.5中的一个已知问题：包含虚拟产品的多送货订单无法正确处理。
exl-id: 34ce79a2-5157-492b-8ee4-bdc09aae0c40
feature: Orders, Products, Shipping/Delivery
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Adobe Commerce 2.3.5已知问题：虚拟产品多发运订单

本文说明了Adobe Commerce 2.3.5中的一个已知问题：包含虚拟产品的多送货订单无法正确处理。

## 受影响的产品和版本

* Adobe Commerce内部部署2.3.5
* 云基础架构上的Adobe Commerce 2.3.5

## 问题

<u>重现步骤</u>：

1. 在店面，将物理和虚拟产品添加到购物车。
1. 继续签出并选择&#x200B;**使用多个地址签出**。
1. 添加所有必需的信息并下订单。

<u>预期的结果</u>：

已成功下达所有产品的订单。

<u>实际结果</u>：

虚拟产品的订单为空。

## 修复

Adobe Commerce 2.3.6中将会提供相应的修复，该版本计划于2020年第4季度发布。

## 相关阅读

在我们的支持知识库中：

* [Adobe Commerce 2.3.5中的产品比较已知问题](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5中的批量操作产品计数已知问题](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5和2.3.5-p1中的国家/地区支付方法问题](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

在我们的开发人员文档中：

* [Adobe Commerce 2.3.5发行说明](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
