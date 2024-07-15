---
title: 'Adobe Commerce 2.4.2 B2B：折扣仍按支付方法更改'
description: 本文介绍了一个已知的Adobe Commerce 2.4.2 B2B问题，该问题在结账时更改支付方式后仍存在与支付方式关联的折扣。 目前没有可用的解决方案。
exl-id: cd863852-403b-404f-8717-c78c238f5f33
feature: B2B, Orders, Payments, Personalization
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B：折扣仍按支付方法更改

本文介绍了一个已知的Adobe Commerce 2.4.2 B2B问题，该问题在结账时更改支付方式后仍存在与支付方式关联的折扣。 目前没有可用的解决方案。

## 受影响的产品和版本

* Adobe Commerce 2.4.2
* 云基础架构上的Adobe Commerce 2.4.2
* 适用于Adobe Commerce 1.3.1的B2B


## 问题

<u>重现问题的步骤</u> ：

1. 创建与付款方式绑定的购物车&#x200B;**价格规则**（例如：Paypal用户可获得20%的折扣。）
1. 创建采购订单(PO)并选择Paypal作为付款方法。 将应用折扣。
1. PO已审批。
1. 转到付款页面以完成订单。
1. 选择其他付款方式。

<u>实际结果</u> ：

付款方式折扣仍应用于订单合计。  未显示错误消息。商店所有者将能够通过检查订单历史记录看到此情况。

<u>预期结果</u>：付款方式折扣按预期从订单总额中删除。

## 解决方案

目前没有可用的解决方案。
