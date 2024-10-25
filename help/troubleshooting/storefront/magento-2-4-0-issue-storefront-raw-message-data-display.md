---
title: 'Adobe Commerce 2.4.0问题：storefront原始消息数据显示'
description: 当店面上的所有错误消息都使用“+”符号而不是空格显示时，本文为该问题提供了解决方案。 此解决方案有助于保持错误消息可读性。
exl-id: f44fe434-a320-4e7e-a876-9575921749f3
feature: Storefront
role: Admin
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Adobe Commerce 2.4.0问题：storefront原始消息数据显示

当店面上的所有错误消息都使用“+”符号而不是空格显示时，本文为该问题提供了解决方案。 此解决方案有助于保持错误消息可读性。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0。

## 问题

<u>要再现的步骤：</u>

1. 转到店面上的&#x200B;**新建帐户**&#x200B;页面。
1. 使用注册的电子邮件创建新帐户。 将显示以下消息：

`There+is+already+an+account+with+this+email+address.+If+you+are+sure+that+it+is+your+email+address,+click+here+to+get+your+password+and+access+your+account.`

## 原因

该问题是由与set\\read Cookie相关的PHP 7.4.2问题引起的。 请参阅[PHP错误\#79174 setcookie()将空间编码为\`+\`，但$\_COOKIE不再解码它们](https://bugs.php.net/bug.php?id=79174)。

## 解决方案

要解决此问题，请使用另一个版本的PHP 7.4.x。Adobe Commerce 2.4.0不支持PHP 7.4.2。

## 我们的支持知识库中的相关读物：

* [Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题：刷新客户活动不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
