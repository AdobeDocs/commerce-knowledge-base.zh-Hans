---
title: 无法将用户添加到Adobe Commerce云项目
description: 本文提供一种解决方案，用于解决您无法将用户添加到Adobe Commerce云项目的问题。
exl-id: 59940916-bf92-4e89-a6f9-bca87c54125c
feature: Cloud, Paas
role: Developer
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 无法将用户添加到Adobe Commerce云项目

当您尝试将用户添加到云项目时，本文会为您提供解决方案，但失败并出现错误： *用户XXX不存在*。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

本文提供一种解决方案，用于解决您无法将用户添加到Adobe Commerce云项目的问题。

## 原因

这是预期行为。 用户的帐户应首先在https://accounts.magento.cloud创建，并链接到其AdobeSSO，以便作为用户添加到项目中。

## 解决方案

1. 要求用户在https://accounts.magento.cloud上登录其帐户(他们必须已经在adobe.com上在该电子邮件地址下注册了帐户。 在https://account.adobe.com创建/拥有帐户并不自动意味着用户将在https://accounts.magento.cloud拥有帐户)
注意：如果用户在2022年8月之前拥有在account.magento.com或accounts.magento.cloud上的帐户，则他们可能没有在adobe.com上拥有或拥有的帐户，除非他们在2022年8月或之后创建了该帐户。 如果用户确实拥有Adobe帐户并且无法登录，请向[Grp-Magento-HelpCenterLoginIssues@adobe.com](mailto:Grp-Magento-HelpCenterLoginIssues@adobe.com)发送一封包含详细信息的电子邮件。
1. 随后，用户应转到https://accounts.magento.cloud。
1. 完成此操作后，您应该能够将用户添加到项目中。 有关步骤，请参阅我们的Commerce on Cloud Infrastructure指南中的[添加用户和管理访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-users-and-manage-access)。

## 相关阅读：

* 我们的Commerce on Cloud Infrastructure指南中的[管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)。
* [无法登录Adobe Commerce支持或云帐户](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)
