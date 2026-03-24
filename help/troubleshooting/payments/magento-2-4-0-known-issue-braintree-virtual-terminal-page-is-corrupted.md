---
title: Adobe Commerce 2.4.0 Braintree虚拟终端页面已损坏
description: 本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致Braintree虚拟终端页面未加载正确的UI元素，或者如果未配置Braintree，则显示正确的错误消息。
exl-id: 1d4d762d-2ab3-4752-ad6d-1eb6a179917d
feature: Orders, Payments
role: Developer
source-git-commit: 1dcd003bd9b08741c0fba464f5520797cfaeccbb
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 Braintree虚拟终端页面已损坏

本文为已知的Adobe Commerce 2.4.0问题提供了一个修补程序，该问题导致Braintree虚拟终端页面未加载正确的UI元素，或者如果未配置Braintree，则显示正确的错误消息。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

### 场景1：配置Braintree支付方式

<u>要再现的步骤：</u>

在Commerce Admin中，转到&#x200B;**Sales** > **Braintree虚拟终端**。**&#x200B; **

<u>预期结果：</u>

使用正确的UI加载&#x200B;**Braintree虚拟终端**&#x200B;页面。

<u>实际结果：</u>

**Braintree虚拟终端**&#x200B;页面的UI已损坏。

### 场景2：配置Braintree支付方式

<u>要再现的步骤：</u>

在Commerce Admin中，转到&#x200B;**Sales** > **Braintree虚拟终端**。**&#x200B; **

<u>预期结果：</u>

**Braintree虚拟终端**&#x200B;页面加载时带有正确的UI，并显示一条警告，告知您尚未配置Braintree。

<u>实际结果：</u>

**Braintree虚拟终端**&#x200B;页面的UI已损坏，未显示任何警告。

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[BUNDLE-2670-composer.patch](assets/BUNDLE-2670-composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento)提供的编辑器修补程序。

## 附加文件
