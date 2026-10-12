---
title: 当字段变灰时，如何更改magento.com帐户上的电子邮件地址
description: 本文讨论当字段呈灰色时，如何更改[Magento.com](https://account.magento.com)帐户上的电子邮件地址。
exl-id: cd527203-345c-4318-8ca8-0063109b5f79
feature: Communications
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%
---
# 当字段呈灰色时，如何更改magento.com帐户上的电子邮件地址？

本文介绍当字段在以下情况下呈灰色时，如何更改[Magento.com](https://account.magento.com)帐户上的电子邮件地址：

* 您或原始用户已离开公司。
* 您的公司已迁移到新电子邮件域。
* 您正在切换到通讯组列表或捕获所有电子邮件地址。

## 受影响的产品和版本

* 所有Adobe Commerce版本和基础设施类型

## 原因

[Magento.com](https://account.magento.com)帐户上的电子邮件地址已链接到位于<https://account.adobe.com>的Adobe帐户，必须在该位置进行更新。

## 更改电子邮件地址的步骤

### 案例一：

更改在<https://account.adobe.com>拥有自己帐户的用户电子邮件地址

<u>解决方案</u>

1. [在https://experienceleague.adobe.com/home#support上提交支持请求](https://experienceleague.adobe.com/home#support)，声明如下：

   * 要更新的现有电子邮件地址
   * 新电子邮件地址
   * 新帐户的图像ID（如果可用）

1. 请求团队合并两个帐户，以更新现有帐户上的电子邮件地址。

### 案例二：

更改当前在<https://account.adobe.com>没有自己的帐户的用户电子邮件地址

<u>解决方案</u>

如果您有权访问[当前所有者电子邮件]的邮箱，请按照《Creative Cloud用户指南》中的[重置或更改Adobe密码](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html)指南重置当前所有者电子邮件的密码。

1. 找到发送到当前所有者的邮箱的密码重置链接，并附上相关说明。
1. 设置新密码，并将电子邮件更改为[新所有者电子邮件]。
1. 导航到[IMS帐户](https://account.adobe.com/)以使用新电子邮件登录，然后更改密码。
1. 更改电子邮件地址和密码后，导航到[Magento.com](https://account.magento.com)以使用[新所有者电子邮件]登录。

但是，如果您无权访问发送到[当前所有者电子邮件]的电子邮件，请按照以下步骤操作：

1. 使用您公司的邮件服务器配置，设置从[当前所有者电子邮件]到新电子邮件的电子邮件转发。
1. 现在，请继续执行上述步骤。

## 相关阅读

《Creative Cloud用户指南》中的[重置忘记的密码](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html)。
在《Creative Cloud用户指南》中[更新您的帐户配置文件](https://helpx.adobe.com/manage-account/using/edit-adobe-account-personal-profile.html)。
