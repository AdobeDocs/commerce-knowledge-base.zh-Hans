---
title: 如何在支持通知中包含团队成员
description: 本文解释了如何在支持通知中包含团队成员。
feature: Cloud, Support, Admin Workspace
role: Admin, Developer
exl-id: 63ea3f60-a509-447c-ac3d-bb2133141c80
source-git-commit: 771793d45000e65c1bf41137cd984d2977b0a9ff
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# 如何在支持通知中包含团队成员

本文介绍了如何让团队成员通过电子邮件通知自动接收支持更新。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## 原因

* 尚未将该团队成员添加到具有必要权限的[!DNL cloud project]。
* 团队成员没有支持帐户。

## 解决方案

1. 转到&#x200B;**[!DNL Cloud Project URL]**（示例： `https://us-3.magento.cloud/projects/xxxxxx/edit`）。
1. 验证团队成员是否已添加到项目中，并且是[!DNL Super User]。

如果它们尚未添加到项目中，则需要将它们添加为[!DNL Super User]并授予[!DNL Shared Access]：

* 在我们的用户指南中[管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)。
* [无法向Commerce知识库中的Adobe Commerce云项目](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-add-user-adobe-commerce-cloud-project.html)添加用户。
* [Adobe Commerce帮助中心用户指南：在我们的Commerce知识库中共享访问权限](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#shared-access)。

如果他们已添加到[!DNL cloud project]，但没有该[!DNL Super User role]，请在[管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)中相应地更新其[!DNL role]。

## 相关阅读

[前团队成员收到Adobe Commerce Cloud通知电子邮件](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/former-teammembers-receive-cloud-notification-emails.html)
