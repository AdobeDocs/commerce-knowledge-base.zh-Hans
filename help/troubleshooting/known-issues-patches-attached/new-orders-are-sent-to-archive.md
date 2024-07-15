---
title: 新订单将发送到存档
description: 本文为已知的Adobe Commerce 2.2.0问题提供了一个修补程序，该问题与Commerce Admin中新创建的订单显示于存档中而不是Orders网格中有关。
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 新订单将发送到存档

本文为已知的Adobe Commerce 2.2.0问题提供了一个修补程序，该问题与Commerce Admin中新创建的订单显示于存档中而不是Orders网格中有关。

>[!NOTE]
>
>此问题已在2.2.3及更高版本中修复。

## 问题

客户下订单时，订单会显示在存档的订单网格中，而不是常规订单网格中。

<u>重现步骤</u>：

1. 将任何产品添加到店面的购物车中，结帐，然后下订单。
1. 在Commerce管理员中，导航到&#x200B;**销售** > **操作** > **订单**。 查看网格中的显示顺序。
1. 导航到&#x200B;**销售** > **存档** > **订单**。 查看网格中的新顺序。

<u>预期的结果</u>：

订单仅显示在“订单”网格中。

<u>实际结果</u>：

订单显示在“订单”网格和“订单存档”网格中。

## 解决方案

应用修补程序后，订单将按预期显示在“订单”网格中。 但您需要在Commerce管理员中手动恢复在应用修补程序之前发送到archive的内容。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-8007\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce 2.2.0

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce本地、Adobe Commerce on cloud infrastructure 2.2.1 - 2.2.3

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe Commerce提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)。

## 用户指南中的有用链接

* [管理已存档的订单](https://docs.magento.com/user-guide/sales/order-archive.html)

## 附加文件
