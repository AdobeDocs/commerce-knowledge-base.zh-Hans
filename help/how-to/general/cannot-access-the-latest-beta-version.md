---
title: 无法访问最新的Beta版本
description: 本文针对在尝试使用Adobe Commerce的最新Beta版本代码时出现的问题提供了解决方案。 Beta代码仅适用于已遵循[Adobe Beta计划](https://github.com/magento/magento2/wiki/Magento-Beta-Program)中所述过程的官方Adobe Commerce合作伙伴。
exl-id: a53c854e-38a8-4c8c-8586-9d99c576c835
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# 无法访问最新的Beta版本

本文针对在尝试使用Adobe Commerce的最新Beta版本代码时出现的问题提供了解决方案。 Beta代码仅适用于遵循[Adobe计划](https://github.com/magento/magento2/wiki/Magento-Beta-Program)中所述过程的官方Adobe CommerceBeta合作伙伴。

## 问题

本文介绍了以下有关访问早期访问代码的问题：

* Adobe Commerce Beta版本不可在&#x200B;**magento.com**&#x200B;上的&#x200B;**我的帐户** > [下载](https://account.magento.com/customer/account/login)下下载。
* 无法使用Composer从[magento.com](https://account.magento.com/customer/account/login)下载抢先访问的Adobe Commerce版本。

## 原因

这些是导致问题的最常见原因：

* 您在错误的位置查找早期访问代码。
* 您使用了错误的MageID。
* 开发人员需要从正确的MageID获取访问密钥。
* 您的帐户不属于Beta计划。

## 解决方案

### 提前访问代码位置

在测试版访问期间，只能通过[repo.magento.com](https://repo.magento.com/)上的Composer获得发行包。 在此期间，发行包在GitHub和Adobe Commerce门户上不可用，我们将在GA日期将它们发布到这些位置。 有关如何使用Composer的更多详细信息，请单击[此处](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)。

### 您需要使用的图像ID

您必须使用与合作伙伴帐户关联的主MageID。 Beta程序未链接到具有共享访问权限的任何联系人。 早期访问只能通过Composer或与您的合作伙伴许可证关联的MageID通过[repo.magento.com](https://repo.magento.com/)访问。

#### 如何确定我的MageID是否是主要的ID

要确定您的MageID是否为主映像，请尝试以下操作：

1. 登录[magento.com](https://account.magento.com/customer/account/login)并转到&#x200B;**我的产品和服务**&#x200B;选项卡。 在Partners子部分中，检查您是否看到有效的Partner许可证信息：
   * 如果您看到有效的Partner许可证信息，则表示您的MageID是主要的。 如果END DATE值是未来的日期，则合作伙伴许可证有效。
   * 如果您看不到有效的合作伙伴许可证信息，则您的MageID仅具有共享访问权限。 要了解谁是主ID持有者，请转到&#x200B;**与我共享**&#x200B;注意此处指定的SHARENAME。 单击&#x200B;**切换帐户**&#x200B;并选择您在SHARENAME中记下的值。 在欢迎页面上，您将看到主ID持有者的电子邮件。
1. 如果由于任何原因无法在[magento.com](https://account.magento.com/customer/account/login)上找到此信息，请联系您的合作伙伴经理。
1. 如果以上都不起作用，请[联系支持人员](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)。

#### 开发人员没有正确的密钥访问权限

如果您是主要MageID所有者并需要向团队中的开发人员授予访问权限，请执行以下步骤：

1. 让主MageID所有者登录到[account.magento.com](https://account.magento.com/customer/account/login)。
1. 选择&#x200B;**市场**&#x200B;选项卡，然后单击&#x200B;**访问密钥**。
1. 选择&#x200B;**创建新的访问密钥**&#x200B;并将其命名为。
1. 将密钥发送给开发人员。

### 不是抢先体验计划的一部分

我们的Beta访问计划仅适用于我们的解决方案和技术合作伙伴，以便他们能够评估我们的预生产代码。 要纳入Beta Access计划，贵组织必须拥有一个信誉良好的有效Adobe合作伙伴帐户，并在[此处](https://github.com/magento/magento2/wiki/Magento-Beta-Program)签署Beta NDA。 如果您认为您符合这些条件并且无法访问测试版代码，请联系[commercebeta@adobe.com](mailto:commercebeta@adobe.com)。
