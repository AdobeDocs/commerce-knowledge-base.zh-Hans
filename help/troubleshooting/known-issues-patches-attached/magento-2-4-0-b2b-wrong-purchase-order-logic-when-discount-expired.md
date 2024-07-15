---
title: 'Adobe Commerce 2.4.0 B2B：折扣过期时采购订单逻辑错误'
description: 本文为Adobe Commerce 2.4.0 B2B中不适用的采购订单(PO)折扣的已知问题提供了一个修补程序。 如果PO的折扣代码在PO处于审批流程时过期，则批准的订单不会反映折扣。
exl-id: 3ef41655-c31e-4e9c-8985-fa1b4fd53170
feature: B2B, Orders, Payments, Personalization, Purchase Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B：折扣过期时采购订单逻辑错误

本文为Adobe Commerce 2.4.0 B2B中不适用的采购订单(PO)折扣的已知问题提供了一个修补程序。 如果PO的折扣代码在PO处于审批流程时过期，则批准的订单不会反映折扣。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 问题

<u>先决条件</u>：创建了折扣优惠券，并且存在阻止自动处理PO的审批规则。

<u>要再现的步骤：</u>

1. 下达应用了折扣的采购单。
1. 停用折扣优惠券。
1. 将PO审批为经理。
1. 检查作为结果创建的订单。

<u>预期结果：</u>

订单创建时带有折扣总计。

<u>实际结果：</u>

订单是按全部金额创建的。

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[B2B-709-composer.patch](assets/B2B-709-composer.patch.zip)

该修补程序还能够以两种格式下载： [Adobe Commerce下载](https://magento.com/tech-resources/download)页左侧列导航栏中&#x200B;**修补程序**&#x200B;下的`.git`和`.composer`。 搜索XXX修补程序。

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
