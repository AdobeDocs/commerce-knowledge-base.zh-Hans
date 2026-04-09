---
title: 更改当前的Adobe帐户电子邮件地址
description: 了解如何将当前在Adobe帐户中注册的电子邮件地址更改为当前未在Adobe帐户或Magento帐户中注册的新地址。
exl-id: ca549d38-0d62-4206-9727-0ed85b733dc3
feature: Communications
source-git-commit: 8d91d4c21dc981accf25537cdb61e1271e17b78c
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 更改当前的Adobe帐户电子邮件地址

本文说明如何将当前在[Adobe帐户](https://account.adobe.com/)中注册的电子邮件地址更改为当前未在[Adobe帐户](https://account.adobe.com/)或[Magento帐户](https://account.magento.com/)中注册的新地址。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法和版本）

## 先决条件

新电子邮件地址的所有者必须有权访问当前电子邮件地址。

如果您无权访问当前电子邮件地址，请使用公司邮件服务器配置设置从当前所有者的电子邮件转发到新电子邮件的电子邮件转发。

## 更改电子邮件地址的步骤

按照以下步骤更改电子邮件地址：

1. 重置用于旧电子邮件地址的密码。 按照Adobe helpx中的[重置忘记的密码](https://helpx.adobe.com/cn/manage-account/using/change-or-reset-password.html)中提供的说明进行操作。
1. 密码重置链接将发送到当前所有者的邮箱，并附上相关说明。
1. 导航到[Adobe帐户页面](https://account.adobe.com)以使用新电子邮件登录并设置密码。

## 重要信息：云帐户用户名未自动更新

如果您在云基础架构上使用Adobe Commerce，则更改Adobe帐户上的电子邮件地址或MAGE ID不会自动更新您的[云帐户](https://accounts.magento.cloud)中显示的用户名。

完成本文中的步骤以更改Adobe帐户电子邮件地址后：

1. 在[https://accounts.magento.cloud](https://accounts.magento.cloud)登录到您的Cloud帐户。
1. 按照支持知识库中[如何更新云帐户配置文件](/help/how-to/general/how-to-update-the-cloud-account-profile.md)中的步骤手动更新云帐户配置文件（用户名）。

这可确保您的Cloud帐户用户名与更新后的Adobe或MAGE ID电子邮件保持一致，并避免在访问云项目或接收系统通知时造成混淆。

## 在电子邮件更改后验证市场和支持访问权限

在更改MAGE ID的电子邮件地址后，您还必须完成以下步骤以确保Adobe Commerce Marketplace和支持可以正确识别您的新电子邮件：

### 验证Commerce Marketplace电子邮件

1. 登录到您的Commerce Marketplace帐户，并确认您的帐户电子邮件已更新为新地址。
1. 如果电子邮件未更新，请提交[支持票证](https://experienceleague.adobe.com/zh-hans/support#home)以请求更正Commerce Marketplace帐户电子邮件。

### 请求支持人员完成内部帐户更新

1. 提交[支持票证](https://experienceleague.adobe.com/zh-hans/support#home)，要求我们完成任何必要的内部更新（例如，更新旧的Adobe ID和新的ID与图像ID之间的关联）。
1. 如果由于Commerce Marketplace电子邮件在上一部分中未更新而打开了支持票证，则可以使用同一票证来请求这些额外的内部更新。
