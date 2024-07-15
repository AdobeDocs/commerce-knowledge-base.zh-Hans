---
title: Adobe Commerce 2.4.0中的配送标签创建已知问题
description: 本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致无法创建送货标签。
exl-id: 722689d9-0c90-4a9d-8449-e93c6585b7c3
feature: Orders, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Adobe Commerce 2.4.0中的配送标签创建已知问题

本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致无法创建送货标签。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>先决条件</u>：使用FedEx、DHL、UPS或USPS配送方式创建订单。

### 方案1：添加发运时创建标签

<u>要再现的步骤：</u>

1. 在Admin中打开&#x200B;**Sales** > **Orders**&#x200B;下的已下订单。
1. 单击&#x200B;**发货**&#x200B;按钮。 将打开&#x200B;**新装运**&#x200B;页。

<u>预期结果：</u>

**创建送货标签**&#x200B;复选框显示在页面底部。

<u>实际结果：</u>

未显示&#x200B;**创建送货标签**&#x200B;复选框。

### 方案2：为现有发运创建标签

<u>要再现的步骤：</u>

1. 在Admin中打开&#x200B;**Sales** > **Orders**&#x200B;下的已下订单。
1. 单击&#x200B;**发货**&#x200B;按钮。 将打开&#x200B;**新装运**&#x200B;页。
1. 单击&#x200B;**提交装运**&#x200B;按钮。 已创建装运。
1. 打开新创建的装运。
1. 单击&#x200B;**创建送货标签**&#x200B;按钮。 将打开&#x200B;**创建包**&#x200B;对话框。

<u>预期结果：</u>

**创建包**&#x200B;模式窗口上的&#x200B;**将产品添加到包**&#x200B;按钮显示包含订单项的字段。

<u>实际结果：</u>

未正确显示&#x200B;**创建包**&#x200B;模式窗口，无法将订单项目添加到装运。

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[MC-35514-2.4.0-CE-composer-2.patch](assets/MC-35514-2.4.0-CE-composer-2.patch.zip)

该修补程序还能够以两种格式（`.git`和`.composer`）下载，它们位于[Adobe Commerce Downloads](https://magento.com/tech-resources/download)页左侧列导航栏中&#x200B;**修补程序**&#x200B;下。 搜索MC-35514修补程序。

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce版本2.4.0
* Adobe Commerce内部部署版本2.4.0

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
