---
title: 无法访问最新的Adobe Commerce预发行版
description: 本文为尝试使用Adobe Commerce的最新预发行版代码时出现的问题提供了解决方案。
exl-id: cbf54a15-b307-4bfc-90b7-cff98aeb4fce
feature: Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# 无法访问最新的Adobe Commerce预发行版

本文为尝试使用Adobe Commerce的最新预发行版代码时出现的问题提供了解决方案。

>[!NOTE]
>
>如果您在访问Beta时遇到问题，请参阅[无法访问最新的Beta版本](/help/how-to/general/cannot-access-the-latest-beta-version.md)一文。

## 问题

本文介绍了以下有关访问预发行版代码的问题：

* 找不到预发行版代码。
* 无法使用Composer从[magento.com](https://account.magento.com/customer/account/login)下载抢先访问的Adobe Commerce版本。

## 原因

这些是导致问题的最常见原因：

* 您在错误的位置查找早期访问代码。
* 通过编辑器访问代码时，您使用了错误的MageID。
* 您的帐户不属于预发行计划。

## 解决方案

### 提前访问代码位置

在预发行期间，发行版软件包在以下两个位置提供：

1. 通过[magento.com](https://repo.magento.com/)上的Composer，使用帐户的主MageID。 有关如何使用编辑器的更多详细信息，请参阅我们的开发人员文档中的[使用编辑器安装Adobe Commerce](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/composer)。
1. 在[account.magento.com](https://account.magento.com/customer/account/login)上，**我的帐户** > **下载**。

>[!NOTE]
>
>在GA发布日期之前，发行包在GitHub上不可用。

### 您需要使用的图像ID

您必须使用与您的Adobe Commerce或合作伙伴帐户关联的主MageID。 预发行计划未链接到具有共享访问权限的任何联系人。 早期访问只能通过与Adobe Commerce许可证或合作伙伴许可证关联的MageID通过Composer或[repo.magento.com](https://repo.magento.com/)访问。

#### 如何确定我的MageID是否是主要的ID？

**对于商家**

要确定您的MageID是否为主映像，请尝试以下操作：

1. 登录[magento.com](https://account.magento.com/customer/account/login)并转到&#x200B;**我的产品和服务**&#x200B;选项卡。 如果您在该处看到Adobe Commerce许可证信息，请选中：
   * 如果您看到Adobe Commerce许可证信息，则表示您的MageID是主要的。
   * 如果您没有看到Adobe Commerce许可证信息，则您的MageID仅具有共享访问权限。 要了解谁是主ID持有者，请转到&#x200B;**与我共享**&#x200B;注意此处指定的SHARENAME。 单击&#x200B;**切换帐户**&#x200B;并选择您在SHARENAME中记下的值。 在欢迎页面上，您将看到主ID持有者的电子邮件。
1. 如果由于任何原因无法在[magento.com](https://account.magento.com/customer/account/login)上找到此信息，请联系您的Adobe客户团队。
1. 如果以上都不起作用，请[联系支持人员](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

合作伙伴&#x200B;**&#x200B;**

要确定您的MageID是否为主映像，请尝试以下操作：

1. 登录[magento.com](https://account.magento.com/customer/account/login)并转到&#x200B;**我的产品和服务**&#x200B;选项卡。 在Partners子部分中，检查您是否看到有效的Partner许可证信息：
   * 如果您看到有效的Partner许可证信息，则表示您的MageID是主要的。 如果END DATE值是未来的日期，则合作伙伴许可证有效。
   * 如果您看不到有效的合作伙伴许可证信息，则您的MageID仅具有共享访问权限。 要了解谁是主ID持有者，请转到&#x200B;**与我共享**&#x200B;注意此处指定的SHARENAME。 单击&#x200B;**切换帐户**&#x200B;并选择您在SHARENAME中记下的值。 在欢迎页面上，您将看到主ID持有者的电子邮件。
1. 如果由于任何原因无法在[magento.com](https://account.magento.com/customer/account/login)上找到此信息，请联系您的合作伙伴经理。
1. 如果以上都不起作用，请[с联系支持人员](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

### 不是预发行计划的一部分

要包含在预发布访问计划中，贵组织必须拥有一个信誉良好的有效Adobe Commerce或合作伙伴帐户。 如果您认为您符合此条件并且无法访问预发行版代码，请使用您的MageID [联系支持人员](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
