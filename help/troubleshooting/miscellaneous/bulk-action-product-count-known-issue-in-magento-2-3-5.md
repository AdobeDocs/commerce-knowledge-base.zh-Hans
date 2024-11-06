---
title: Adobe Commerce 2.3.5中的批量操作产品计数已知问题
description: 本文介绍了一个已知的Adobe Commerce 2.3.5问题，该问题导致商家在Admin中的批量操作后收到的通知包含错误数量的受影响项目。
exl-id: 3ede15d4-4c39-442a-8784-2d5e6650fe67
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Adobe Commerce 2.3.5中的批量操作产品计数已知问题

本文介绍了一个已知的Adobe Commerce 2.3.5问题，该问题导致商家在Admin中的批量操作后收到的通知包含错误数量的受影响项目。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.5
* Adobe Commerce内部部署2.3.5

## 问题

批量操作（例如，批量产品更新或导入/导出）后Adobe Commerce显示的系统消息显示为0，而不是受批量操作影响的产品的准确计数。

## 修复

Adobe Commerce 2.3.6中将会提供相应的修复，该版本计划于2020年第4季度发布。

## 相关阅读

* 适用于Adobe Commerce 2.3.5已知问题的Adobe Commerce支持知识库文章：
   * [在Adobe Commerce 2.3.5中无法正确处理包含虚拟产品的多配送订单](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
   * [Adobe Commerce 2.3.5中的产品比较已知问题](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
   * [Adobe Commerce中的云基础设施国家/地区支付方法问题，以及Adobe Commerce内部部署2.3.5和2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
   * [Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
   * [开发人员文档中的Adobe Commerce 2.3.5已知问题](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
