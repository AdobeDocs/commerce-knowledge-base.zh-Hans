---
title: 'Adobe Commerce 2.4.0：在多送货结帐中删除奖励点时出现404错误'
description: 本文为Adobe Commerce 2.4.0中的一个已知问题提供了解决方法，即在删除多配送结账页面上的奖励点时，出现“*404 Not Found*”网页错误。 目前，在多配送结账页面上，当尝试删除用于支付订单的奖励点时，会显示“*404 Not Found*”页面而不是成功的奖励点取消。 此问题将在Adobe Commerce 2.4.1补丁版本中得以解决。
exl-id: 59de4b3d-af28-4ae8-8f55-4ec958e6ee8b
feature: B2B, Checkout, Orders, Rewards, Shipping/Delivery, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：在多送货结帐中删除奖励点时出现404错误

本文为Adobe Commerce 2.4.0中的一个已知问题提供了解决方法，即在删除多配送结账页面上的奖励点时，出现“*404 Not Found*”网页错误。 目前，在多配送结账页面上，当尝试删除用于支付订单的奖励点时，将显示“*404 Not Found*”页面，而不是成功的奖励点取消。 此问题将在Adobe Commerce 2.4.1补丁版本中得以解决。

## 受影响的产品和版本

* Adobe Commerce 2.4.0（所有部署方法）

## 问题

<u>重现步骤</u>

1. 导航到店面并以客户身份登录。
1. 将至少两个产品添加到&#x200B;**购物车**。
1. 打开&#x200B;**迷你购物车**。
1. 单击&#x200B;**查看和编辑购物车**&#x200B;链接。
1. 单击&#x200B;**使用多个地址签出**&#x200B;链接。
1. 在&#x200B;**收货地址**&#x200B;页面上选择配送地址。
1. 单击&#x200B;**转到送货信息**&#x200B;按钮。
1. 为每个地址选择&#x200B;**统一费率 — 固定配送方式**。
1. 单击&#x200B;**继续查看帐单信息**&#x200B;按钮。
1. 在&#x200B;**帐单信息**&#x200B;页面上选中&#x200B;**使用您的奖励积分**&#x200B;复选框。
1. 单击&#x200B;**转到查看订单**&#x200B;按钮。
1. 单击任何地址的&#x200B;**Remove**&#x200B;链接以删除奖励积分。

<u>预期的结果</u>

* 此时应会显示&#x200B;**购物车**&#x200B;页面。
* “*您从此订单中删除了奖励积分。* ”消息应会出现。

<u>实际结果</u>

出现“*404 Not Found*”错误页面。

## 解决方法

解决方法是让购买者导航回&#x200B;**购物车**，并从&#x200B;**购物车**&#x200B;网页中删除奖励积分。 Adobe Commerce版本2.4.1修补程序预计将于2020年第4季度发布，可解决此问题。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Storefront上显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
