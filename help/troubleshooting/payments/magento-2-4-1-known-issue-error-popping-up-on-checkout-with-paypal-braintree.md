---
title: Adobe Commerce 2.4.1已知问题：使用PayPal Braintree结帐时弹出错误
description: 本文介绍了一个已知的Adobe Commerce 2.4.1问题，如果使用PayPal Braintree支付并选择多个地址装运，则会在结账的计费步骤中弹出并消失一条错误消息。
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%
---
# Adobe Commerce 2.4.1已知问题：使用PayPal Braintree结帐时弹出错误

本文介绍了一个已知的Adobe Commerce 2.4.1问题，如果使用PayPal Braintree支付并选择多个地址装运，则会在结账的计费步骤中弹出并消失一条错误消息。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.1
* Adobe Commerce内部部署2.4.1

## 问题

如果使用PayPal Braintree付款并选择多个地址装运，则会在结账的计费步骤中弹出并消失错误消息。

<u>要再现的步骤：</u>

1. 在店面，以客户身份登录（如果已在管理员中启用，则可选择作为访客结帐）。
1. 将产品添加到购物车。
1. 单击以打开购物车预览。
1. 单击&#x200B;**查看和编辑购物车**。
1. 在购物车页面上，单击&#x200B;**使用多个地址签出**。
1. 单击&#x200B;**转到送货信息**&#x200B;并指定地址。
1. 单击&#x200B;**继续查看帐单信息**。
1. 选择&#x200B;**PayPal Braintree**&#x200B;并单击&#x200B;**PayPal**&#x200B;按钮。
1. 在弹出窗口中，单击&#x200B;**同意并付款**。

<u>预期结果：</u>

下订单时没有出现错误。

<u>实际结果：</u>

已下订单，但出现错误。 无法初始化&#x200B;*PayPal签出。 请联系商店所有者*。  错误显示一秒钟，然后消失。

## 修复

由于未阻止下订单，因此无需执行解决步骤。
