---
title: Adobe Commerce 2.4.1和2.3.6 “创建帐户”按钮禁用的修补程序
description: 当您在表单上的任何字段输入不正确的值后难以创建新帐户时，本文提供了此问题的修补程序。 例如，当以错误的格式输入电子邮件地址，或者将名字或姓氏字段留空或不输入符合密码要求的值时。 第1季度版本（2.4.2、2.4.1-p1和2.3.6-p1）中将包含永久修复。
exl-id: e6e65ede-8156-4e2b-b369-b18395bb3dbf
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Adobe Commerce 2.4.1和2.3.6 “创建帐户”按钮禁用的修补程序

当您在表单上的任何字段输入不正确的值后难以创建新帐户时，本文提供了此问题的修补程序。 例如，当以错误的格式输入电子邮件地址，或者将名字或姓氏字段留空或不输入符合密码要求的值时。 第1季度版本（2.4.2、2.4.1-p1和2.3.6-p1）中将包含永久修复。

## 问题

此 **创建帐户** 上的按钮 **创建新帐户** 如果购物者输入了无效数据，页面将保持禁用状态。 这样可防止购物者在出错后重新尝试创建帐户。

<u>重现问题的步骤</u>：

1. 转到 **新建客户帐户**.
1. 填写表单字段。 在 **密码** 字段，输入值不符合密码要求。 例如：
   * 中的密码 **密码** 和 **确认密码** 字段不匹配。
   * 中的密码 **密码** 和 **确认密码** 字段不够长。
1. 单击 **创建帐户** 按钮。

<u>预期结果</u>：

* **创建帐户** 按钮应保持活动/启用状态。
* 用户应该能够创建新帐户。

<u>实际结果</u>：

* **创建帐户** 即使使用有效/正确数据填写了所有必填字段后，按钮仍保持禁用状态。
* 客户无法创建新帐户。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接： [下载MC-38509-composer.patch](assets/MC-38509-composer.patch.zip)

## 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Cloud Infrastructure 2.3.6和2.4.1上的Adobe Commerce。
* Adobe Commerce内部部署2.3.6和2.4.1。

该修补程序与任何其他Adobe Commerce版本和版本不兼容。

## 如何应用修补程序

请参阅 [如何应用Adobe提供的编辑器修补程序](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) 以获取说明。

## 相关阅读

* [GitHub Adobe Commerce >提交无效的创建帐户表单会禁用提交按钮](https://github.com/magento/magento2/issues/30513)
* [Adobe Commerce用户指南>快速入门>创建帐户](https://docs.magento.com/user-guide/magento/magento-account-create.html)
