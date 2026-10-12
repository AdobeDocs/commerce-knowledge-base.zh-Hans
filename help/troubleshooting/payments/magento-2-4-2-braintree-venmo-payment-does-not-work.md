---
title: Adobe Commerce 2.4.2：Braintree Venmo付款不起作用
description: 本文介绍了一个已知的Adobe Commerce 2.4.2问题，即在结账期间使用Braintree Venmo时不会生成订单。 目前没有可用的解决方案。
exl-id: 1832ab64-5024-444b-915e-473b34979a6e
feature: Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%
---
# Adobe Commerce 2.4.2：Braintree Venmo付款不起作用

本文介绍了一个已知的Adobe Commerce 2.4.2问题，即在结账期间使用Braintree Venmo时不会生成订单。 目前没有可用的解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.4.2

## 问题

<u>前提条件</u> ：

在Braintree配置中启用Venmo支付。

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

当客户从Venmo应用程序重定向回应用商店，并且订单按预期在Braintree中创建后，将在Adobe Commerce中创建订单。

## 解决方案

目前没有可用的解决方案。
