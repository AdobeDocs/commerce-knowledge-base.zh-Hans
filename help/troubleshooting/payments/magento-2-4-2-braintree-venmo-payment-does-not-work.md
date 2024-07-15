---
title: 'Adobe Commerce 2.4.2：BraintreeVenmo付款不起作用'
description: 本文介绍了一个已知的Adobe Commerce 2.4.2问题，即在结账期间使用BraintreeVenmo时不会生成订单。 目前没有可用的解决方案。
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Adobe Commerce 2.4.2：BraintreeVenmo付款不起作用

本文介绍了一个已知的Adobe Commerce 2.4.2问题，即在结账期间使用BraintreeVenmo时不会生成订单。 目前没有可用的解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.4.2

## 问题

<u>前提条件</u> ：

在Braintree配置中启用Venmo付款。

<u>重现问题的步骤</u> ：

1. 在店面，添加任何商品到购物车。
1. 继续执行&#x200B;**签出**。
1. 选择适当的配送方式。
1. 选择&#x200B;**Venmo**&#x200B;作为付款方式。
1. 单击&#x200B;**使用Venmo**&#x200B;付款。
1. 单击&#x200B;**下订单**。

<u>实际结果</u>：

将客户从Venmo应用程序重定向回应用商店后，不会在Adobe Commerce代码中创建订单，并且不会显示错误消息。 订单是在Braintree中创建的。

<u>预期的结果</u>：

当客户从Venmo应用程序重定向回应用商店，并且订单是按预期在Braintree中创建后，将在Adobe Commerce中创建订单。

## 解决方案

目前没有可用的解决方案。
