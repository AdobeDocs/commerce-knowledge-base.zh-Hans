---
title: 'Adobe Commerce 2.4.0、2.4.1：启用BraintreeVenmo部分发票'
description: 本文介绍了已知的Adobe Commerce 2.4.0和2.4.1问题，该问题不适用于通过Venmo使用Braintree下单的订单。
exl-id: ef6c8aa4-a2a7-4e07-a957-23173017baf2
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0、2.4.1：启用BraintreeVenmo部分发票

本文介绍了已知的Adobe Commerce 2.4.0和2.4.1问题，该问题不适用于通过Venmo使用Braintree下单的订单。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0和2.4.1
* 云基础架构上的Adobe Commerce 2.4.0和2.4.1

## 问题

<u>先决条件：</u>

在Braintree付款方式配置中，设置&#x200B;**通过Braintree启用Venmo** = *是*，付款操作&#x200B;**为** = *授权*；**为卡付款启用保管库** = *否*。

<u>要再现的步骤：</u>

1. 使用Venmo(Braintree)作为付款方式，为两种或更多种产品创建订单。
1. 在Commerce管理中打开订单。
1. 为订购的产品之一创建发票。
1. 尝试为其余订购的产品创建发票。

<u>预期结果：</u>

已创建发票。

<u>实际结果：</u>

显示以下错误消息： *“vault\_capture”命令不存在。 请验证该命令并重试。*

## 解决方法

在为使用Braintree通过Venmo下达的订单创建发票时获取全部金额。
