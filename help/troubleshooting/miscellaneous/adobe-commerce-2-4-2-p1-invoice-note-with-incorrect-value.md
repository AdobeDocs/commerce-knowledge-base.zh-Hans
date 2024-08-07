---
title: 'Adobe Commerce 2.4.2-p1：具有不正确值的发票注释'
description: 本文介绍了已知的Adobe Commerce 2.4.2-p1问题，该问题导致在创建订单时更改客户组时生成值不正确的发票注释。 此问题已在版本2.4.3中修复。
exl-id: bde90251-625f-4c9d-8e5a-9a2019656125
feature: Customer Service, Invoices
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Adobe Commerce 2.4.2-p1：具有不正确值的发票注释

本文介绍了已知的Adobe Commerce 2.4.2-p1问题，该问题导致在创建订单时更改客户组时生成值不正确的发票注释。 此问题已在版本2.4.3中修复。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.2-p1
* 云基础架构上的Adobe Commerce 2.4.2-p1

## 问题

如果在创建订单时更改了客户组，则会使用不正确的发票备注生成发票。

<u>重现步骤</u>：

1. 创建&#x200B;**测试客户帐户**&#x200B;并将其添加到&#x200B;**零售客户组**。
1. 为测试客户创建&#x200B;**新订单**，添加&#x200B;**产品**&#x200B;和&#x200B;**地址**。
1. 选择&#x200B;**配送方式**。
1. 在&#x200B;**帐户信息**&#x200B;部分中，将客户组从&#x200B;**零售商**&#x200B;更改为&#x200B;**政府**。
1. 单击&#x200B;**下单**。
1. 单击&#x200B;**发票** > **提交发票**。

<u>预期的结果</u>：

以下注释应出现在此订单的&#x200B;**注释**&#x200B;部分下：“已成功发送顶点发票。 金额：$0.00。”

<u>实际结果</u>：

此订单的&#x200B;**备注**&#x200B;部分下面显示了以下备注：“已成功发送顶点发票。 金额：3.23美元。”

## 解决方案

此问题已在版本2.4.3中修复。
