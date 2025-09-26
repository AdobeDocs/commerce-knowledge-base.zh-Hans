---
title: Adobe Commerce 2.4.0：无法刷新客户的活动
description: 本文为管理员用户为客户创建订单并且客户的“活动”侧面板上的“刷新”按钮不起作用时Adobe Commerce 2.4.0已知问题提供了解决方案。
exl-id: 50048e9f-6009-4db5-ae4a-c35a84cec265
feature: Configuration
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Adobe Commerce 2.4.0：无法刷新客户的活动

本文为管理员用户为客户创建订单并且客户的“活动”侧面板上的“刷新”按钮不起作用时Adobe Commerce 2.4.0已知问题提供了解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>重现步骤</u>：

1. 转到&#x200B;**管理员面板** > **销售额** > **订单**。
1. 单击&#x200B;**新建订单**&#x200B;按钮。
1. 选择已创建的客户。
1. 以创建的客户身份转到店面。
1. 转到&#x200B;**产品**&#x200B;页面。 单击&#x200B;**客户活动**&#x200B;的&#x200B;**最近查看的产品**&#x200B;部分中的&#x200B;**刷新**&#x200B;按钮。
1. 回到店面。
1. 使用创建的产品下订单。
1. 返回&#x200B;**管理员面板**，然后单击&#x200B;**客户活动**&#x200B;的&#x200B;**上次订购的项目**&#x200B;部分的&#x200B;**刷新**&#x200B;按钮。
1. 回到店面。 将创建的产品添加到&#x200B;**比较列表**。
1. 返回&#x200B;**管理面板**。 单击&#x200B;**客户活动**&#x200B;的&#x200B;**比较列表中的产品**&#x200B;部分的&#x200B;**刷新**&#x200B;按钮。
1. 回到店面。
1. 从&#x200B;**比较列表**&#x200B;中删除创建的产品。
1. 返回&#x200B;**管理面板**。
1. 单击&#x200B;**客户活动**&#x200B;的&#x200B;**最近比较的产品**&#x200B;部分的&#x200B;**刷新**&#x200B;按钮。
1. 回到店面。

<u>预期的结果</u>：

产品名称应显示在&#x200B;**最近查看的产品**、**最近订购的项目**、**比较列表中的产品**&#x200B;和&#x200B;**最近比较的产品**&#x200B;部分中。

<u>实际结果</u>：

每次单击&#x200B;**刷新**&#x200B;按钮时都会滚动页面。 产品的名称未显示在相应的部分中。

## 解决方案

解决方法是管理员用户可以通过单击侧边栏底部的&#x200B;**Update Changes**&#x200B;按钮来更新&#x200B;**客户的活动**。 计划在Adobe Commerce 2.4.1修补程序中解决此问题。

![mceclip0.png](assets/mceclip0.png)

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：Braintree支付方法未出现在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
