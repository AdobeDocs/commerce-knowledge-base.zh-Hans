---
title: Adobe Commerce 2.4.0：“将选定内容添加到购物车”不起作用
description: 本文提供了在管理客户的购物车时，Commerce管理员中已知问题中断按钮的解决方法。 当尝试将选定产品添加到客户的购物车时，位于部分底部的**将选定内容添加到我的购物车**按钮不起作用。 此问题出现在包含两个**将选定内容添加到我的购物车**按钮的任何“管理员”面板页面上。 Adobe Commerce 2.4.1中将提供永久修复。
exl-id: b0830ec2-2aea-4afb-8d02-e9c8f54283be
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：“将选定内容添加到购物车”不起作用

本文提供了在管理客户的购物车时，Commerce管理员中已知问题中断按钮的解决方法。 当尝试将选定产品添加到客户的购物车时，位于部分底部的&#x200B;**将选定内容添加到我的购物车**&#x200B;按钮不起作用。 此问题出现在任何包含两个&#x200B;**将选定内容添加到我的购物车**&#x200B;按钮的管理面板页面上。 Adobe Commerce 2.4.1中将提供永久修复。

## 受影响的产品和版本

* Adobe Commerce 2.4.0（所有部署方法）

## 问题

<u>重现步骤</u>

1. 导航到包含两个&#x200B;**将选定内容添加到我的购物车**&#x200B;按钮的任意“管理”面板页面。
1. 选择要添加到我的购物车的项目。
1. 单击位于部分底部的&#x200B;**将选定内容添加到我的购物车**&#x200B;按钮。

<u>预期的结果</u>

所有选择都将按预期添加到我的购物车。

<u>实际结果</u>

Adobe Commerce不会将您的选择添加到我的购物车。

## 解决方案

位于页面顶部的&#x200B;**将选定内容添加到我的购物车**&#x200B;按钮仍在工作。 Adobe Commerce版本2.4.1中预计会在第4.1季度发布此问题。

## 相关阅读

* [MerchDocs&#39;管理用户指南中的购物车](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage)。
* [Adobe Commerce 2.4.0已知问题：在我们的支持知识库中，导出税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)。
* [Adobe Commerce 2.4.0已知问题： Braintree付款方法未出现在我们的支持知识库的“多个地址”结帐中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)。
