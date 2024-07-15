---
title: 'Adobe Commerce 2.4.4：无法创建部分发票'
description: 当用户使用Apple Pay或Google Pay通过Braintree支付作为付款方式时，无法创建部分发票的问题修补程序。
exl-id: bf78cc07-9dc7-4eb8-bfdf-57ea5131effb
feature: Invoices, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Adobe Commerce 2.4.4：无法创建部分发票

当用户使用Apple Pay或Google Pay通过Braintree支付作为付款方式时，无法创建部分发票的问题修补程序。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.4

## 问题

使用Apple Pay或Google Pay作为付款方法时，用户会收到错误“*‘vault_capture’命令不存在。 请验证命令并重试。创建部分发票时为“*”。

<u>重现步骤</u>：

1. 打开您的Adobe Commerce网站。
1. 将简单产品添加到购物车（数量2）。
1. 选择&#x200B;**Apple Pay**&#x200B;或&#x200B;**Google Pay**&#x200B;作为购物车的付款方式。
1. 下订单。
1. 从后端打开订单详细信息。
1. 创建部分发票。
1. 为剩余金额创建另一张发票。

<u>预期的结果</u>：

创建部分发票。

<u>实际结果</u>：

创建第一张部分发票。 创建第二个部分发票时，用户收到以下错误：*“vault_capture”命令不存在。 请验证该命令并重试*。

## 原因

Adobe Commerce将信用卡详细信息保存在保管库中，以创建部分发票。 目前，无法保险库Apple Pay和Google Pay。

## 解决方案

要解决此问题，请应用以下修补程序：

[Braintree_disabled_partial_capture_for_applepay_googlepay.zip](assets/braintree-disabled-partial-capture-for-applepay-googlepay.zip)

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
