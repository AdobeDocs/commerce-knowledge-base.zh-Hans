---
title: 'Adobe Commerce 2.4.1已知问题：使用PayPalBraintree结帐时弹出错误'
description: 本文介绍了一个已知的Adobe Commerce 2.4.1问题，如果使用PayPalBraintree支付并选择多个地址装运，则会在结账的计费步骤中弹出并消失一条错误消息。
exl-id: db3830b2-4885-4d89-85cd-bdcbd4b396e6
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Adobe Commerce 2.4.1已知问题：使用PayPalBraintree结帐时弹出错误

本文介绍了一个已知的Adobe Commerce 2.4.1问题，如果使用PayPalBraintree支付并选择多个地址装运，则会在结账的计费步骤中弹出并消失一条错误消息。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.1
* Adobe Commerce内部部署2.4.1

## 问题

如果使用PayPalBraintree付款并且选择了多个地址装运，则会在结帐的计费步骤中弹出并消失错误消息。

<u>要再现的步骤：</u>

1. 在店面，以客户身份登录（如果已在管理员中启用，则可选择作为访客结帐）。
1. 将产品添加到购物车。
1. 单击以打开购物车预览。
1. 单击&#x200B;**查看和编辑购物车**。
1. 在购物车页面上，单击&#x200B;**使用多个地址签出**。
1. 单击&#x200B;**转到送货信息**&#x200B;并指定地址。
1. 单击&#x200B;**继续查看帐单信息**。
1. 选择&#x200B;**PayPalBraintree**&#x200B;并单击&#x200B;**PayPal**&#x200B;按钮。
1. 在弹出窗口中，单击&#x200B;**同意并付款**。

<u>预期结果：</u>

下订单时没有出现错误。

<u>实际结果：</u>

已下订单，但出现错误。 无法初始化&#x200B;*PayPal签出。 请联系商店所有者*。  错误显示一秒钟，然后消失。

## 修复

由于未阻止下订单，因此无需执行解决步骤。
