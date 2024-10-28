---
title: 在Adobe Commerce 2.3.5中结账时出现商店信用问题
description: 本文针对在Adobe Commerce 2.3.5中结账期间出现的已知商店信用相关问题提供了解决方法，即购物者在选择并随后删除商店信用使用情况后在结账期间遇到错误。 Adobe Commerce 2.3.6中将提供永久修复。
exl-id: a0cca226-4d95-40b3-bd37-f13d28591366
feature: Checkout, Orders, Storefront
role: Admin
source-git-commit: d51fd4d7b064b8eea6cd3771af279b74a8bdec48
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# 在Adobe Commerce 2.3.5中结账时出现商店信用问题

本文针对在Adobe Commerce 2.3.5中结账期间出现的已知商店信用相关问题提供了解决方法，即购物者在选择并随后删除商店信用使用情况后在结账期间遇到错误。 Adobe Commerce 2.3.6中将提供永久修复。

## 受影响的产品和版本

* Adobe Commerce内部部署2.3.5
* 云基础架构上的Adobe Commerce 2.3.5

## 问题

<u>重现步骤</u>：

1. 客户将产品添加到购物车并继续结账。
1. 客户将商店贷记指定为付款方式。
1. 客户删除商店信用并更改付款方式。
1. 客户通过结账进行。

<u>预期的结果</u>：

所有订单信息均正确显示。

<u>实际结果</u>：

Adobe Commerce在订单页面的“订单摘要”部分引发错误。

## 解决方案

客户可以刷新订单页面，订单摘要中的信息将正确加载。 Adobe Commerce 2.3.6中将会提供相应的修复，该版本计划于2020年第4季度发布。

## 相关阅读

Adobe Commerce 2.3.5支持知识库中的已知问题文章：

* [在Adobe Commerce 2.3.5中无法正确处理包含虚拟产品的多配送订单](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)

* [Adobe Commerce中的云基础设施国家/地区支付方法问题，以及Adobe Commerce内部部署2.3.5和2.3.5-p1](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)


* [Adobe Commerce 2.3.5中的批量操作产品计数已知问题](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)

* [Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)

* [Adobe Commerce 2.3.5中的产品比较问题](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)

在我们的开发人员文档中：

* [Adobe Commerce 2.3.5已知问题](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
