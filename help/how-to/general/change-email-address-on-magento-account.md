---
title: 当字段变灰时，如何更改magento.com帐户上的电子邮件地址
description: 本文讨论当字段呈灰色时，如何更改[Magento.com](https://account.magento.com)帐户上的电子邮件地址。
exl-id: cd527203-345c-4318-8ca8-0063109b5f79
feature: Communications
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 当字段呈灰色时，如何更改magento.com帐户上的电子邮件地址？

本文说明当字段为灰色时，如何更改[Magento.com](https://account.magento.com)帐户上的电子邮件地址。

## 受影响的产品和版本

* 所有Adobe Commerce版本和基础设施类型

## 原因

[Magento.com](https://account.magento.com)帐户上的电子邮件地址已链接到位于<https://account.adobe.com>的Adobe帐户，必须在该帐户中更新。

## 更改电子邮件地址的步骤

### 案例一：

更改在<https://account.adobe.com>拥有自己帐户的用户电子邮件地址

<u>解决方案</u>

1. 向Grp-magento-HelpCenterLoginIssues@adobe.com发送电子邮件，说明以下内容：

   * 要更新的现有电子邮件地址
   * 新电子邮件地址
   * 新帐户的图像ID（如果可用）

1. 请求团队合并两个帐户，以更新现有帐户上的电子邮件地址。

### 案例二：

更改当前在<https://account.adobe.com>没有自己的帐户的用户电子邮件地址

<u>解决方案</u>

如果您有权访问[当前所有者电子邮件]的邮箱，请按照《Creative Cloud用户指南》中的[重置或更改您的Adobe密码](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html)指南重置当前所有者电子邮件的密码。

1. 找到发送到当前所有者的邮箱的密码重置链接，并附上相关说明。
1. 设置新密码，并将电子邮件更改为[新所有者电子邮件]。
1. 导航到[IMS帐户](https://account.adobe.com/)以使用新电子邮件登录，然后更改密码。
1. 更改电子邮件地址和密码后，导航到[Magento.com](https://account.magento.com)以使用[新所有者电子邮件]登录。

但是，如果您无权访问发送到[当前所有者电子邮件]的电子邮件，请按照以下步骤操作：

1. 使用您公司的邮件服务器配置，设置从[当前所有者电子邮件]到新电子邮件的电子邮件转发。
1. 现在，请继续执行上述步骤。

## 相关阅读

《Creative Cloud用户指南》中的[重置忘记的密码](https://helpx.adobe.com/manage-account/using/change-or-reset-password.html)。
