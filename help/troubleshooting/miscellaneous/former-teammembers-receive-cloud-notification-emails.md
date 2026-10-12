---
title: 以前的团队成员会收到Adobe Commerce Cloud通知电子邮件
description: 本文为Adobe Commerce提供了一个关于向前团队成员发送云基础架构通知电子邮件的解决方案。
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%
---
# 以前的团队成员会收到Adobe Commerce Cloud通知电子邮件

本文提供了一个解决方案，用于从通知电子邮件的收件人列表中删除满足以下条件的用户：

* 不再与您的项目关联的前团队成员。
* 不应接收通知的当前团队成员。

## 问题

已向您的团队发送有关检测到的中断或云项目/环境的重要问题的通知。 这包括可能不再与您的项目关联的成员，例如外部/代理开发人员或系统集成商。 您希望这些用户停止接收通知。

## 解决方案

>[!NOTE]
>
>如果您是外部/机构开发人员或系统集成商，并且不再与项目相关联，则必须联系项目所有者或项目管理员以获取帮助。

可通过以下两种方法从项目中删除用户来停止通知：

* 方法1：使用云[!DNL Project URL]。 有关步骤，请参阅Commerce on cloud infrastructure指南中的[管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hans)。
* 方法2：使用magento-cloud [!DNL CLI]。 有关步骤，请参阅Commerce on cloud infrastructure指南中的[使用 [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hans#manage-users-with-the-cli)管理用户。

如果此操作已完成，但电子邮件通知仍继续包含这些用户，请提交支持票证以请求从帐户上的&#x200B;*[!UICONTROL Always CC]*&#x200B;设置中删除这些用户。

## 相关阅读

* 在Commerce on cloud infrastructure指南中[查看用户的项目角色](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hans#view-a-user's-project-role)。
* [如何在Commerce KB的支持通知中包含团队成员](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html?lang=zh-Hans)。
