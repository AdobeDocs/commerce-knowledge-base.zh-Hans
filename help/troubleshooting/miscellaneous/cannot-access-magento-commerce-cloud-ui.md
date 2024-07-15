---
title: 无法在云基础架构UI上访问Adobe Commerce
description: 本文针对您无法在Cloud Infrastructure UI上登录Adobe Commerce并收到“403错误”的问题提供了解决方案。
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
source-git-commit: 3d3d2da45d164efbbbaf8c878967caf83f845a59
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 无法在云基础架构UI上访问Adobe Commerce

本文针对无法在云基础架构UI上登录Adobe Commerce并出现&#x200B;*403错误*&#x200B;的问题提供了解决方案。

## 问题

首次尝试在云基础架构UI上登录Adobe Commerce时，您收到&#x200B;*403：环境访问被拒绝*&#x200B;错误。 出现此错误可能是因为首次转到云URL加载主分支，并且您可能无权访问该分支。

## 解决方案

如果您在首次访问URL时遇到403错误，请确保您在主分支中拥有角色。

1. 请联系с项目的许可证所有者或超级用户，确保他们以&#x200B;**环境级别用户**&#x200B;的身份为您提供访问权限，有关说明，请参阅我们的开发人员文档中的[云项目>从Cloud Console管理用户](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-from-the-cloud-console)。

   如果您在特定分支中只有适用的角色，则需要转到该分支的URL，例如
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   下次访问主URL时，它将默认为您访问的最后一个环境。

1. 如果您仍然无法登录，请с联系许可证所有者或项目上的超级用户，确保他们以&#x200B;**项目级别用户**&#x200B;的身份为您提供访问权限，如开发人员文档中的[云项目>将用户添加到项目](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#add-a-user-to-the-project)中所述。
1. 如果错误仍然存在，[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
