---
title: 无法登录Adobe Commerce支持或云帐户
description: 当您难以登录Adobe Commerce支持或云项目时，本文会为您提供解决方案。
exl-id: 676b32d2-8197-4c60-a1b1-3c51b01dd3a3
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%
---
# 无法登录Adobe Commerce支持或云帐户

当您难以登录Adobe Commerce支持或云项目时，本文会为您提供解决方案。

## 受影响的产品和版本

Adobe Commerce（所有部署方法）所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

当您转到[https://account.magento.com/customer/account/login/](https://account.magento.com/customer/account/login/)或[https://accounts.magento.cloud/user](https://accounts.magento.cloud/user)时，您可能会注意到现在有一个统一的登录表单，您无法再像以前一样输入您的凭据。

<u>重现步骤</u>：

尝试登录到您的Commerce帐户。

![adobe-login-one](assets/adobe-login-one.png)

<u>预期的结果</u>：

登录成功。

<u>实际结果</u>：

重定向到使用Adobe帐户登录的页面，且凭据不起作用。

![adobe-login-two](assets/adobe-login-two.png)


## 原因

在我们将Adobe Commerce与其他Adobe解决方案集成的过程中，所有用户都将需要使用连接到其MageID的相同电子邮件地址来创建Adobe登录信息（如果没有）。

## 解决方案

您可以通过以下方式登录到帐户：

- 现有的Adobe公司/个人帐户。
- 如果您没有Adobe帐户，请使用相同的电子邮件地址创建一个帐户。

有关步骤，请参阅Adobe Experience League中的[Commerce Identity Manager](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-identity-manager.html?lang=zh-Hans)。

## 相关阅读

- [链接Magento.com和accounts.magento.cloud帐户登录](/help/faq/general/linking-magento-com-and-accounts-magento-cloud-account-logins.md)
