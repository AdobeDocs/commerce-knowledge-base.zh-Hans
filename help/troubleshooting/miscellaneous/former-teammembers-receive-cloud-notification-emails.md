---
title: 以前的团队成员会收到Adobe Commerce Cloud通知电子邮件
description: 本文为Adobe Commerce提供了一个关于向前团队成员发送云基础架构通知电子邮件的解决方案。
exl-id: b2535f66-8aec-4ddf-9a69-60879a0a1939
feature: Cloud, Communications, Paas
role: Developer
source-git-commit: 0017d43e221ef3023630f714c34aa65b368e214f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# 以前的团队成员会收到Adobe Commerce Cloud通知电子邮件

本文提供了一个解决方案，用于从通知电子邮件的收件人列表中删除满足以下条件的用户：
* 不再与您的项目关联的前团队成员。
* 不应接收通知的当前团队成员。

## 问题

已向您的团队发送有关检测到的中断或云项目/环境的重要问题的通知。 这包括可能不再与您的项目关联的成员，例如外部/代理开发人员或系统集成商。 您希望这些用户停止接收通知。

## 解决方案

可通过以下两种方法从项目中删除用户来停止通知：

* 方法1：使用云[!DNL Project URL]。 有关步骤，请参阅Commerce on cloud infrastructure指南中的[管理用户访问权限](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)。
* 方法2：使用magento-cloud [!DNL CLI]。 有关步骤，请参阅Commerce on cloud infrastructure指南中的[使用 [!DNL CLI]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#manage-users-with-the-cli)管理用户。

如果此操作已完成，但电子邮件通知仍继续包含这些用户，请提交支持票证以请求从帐户上的&#x200B;*[!UICONTROL Always CC]*&#x200B;设置中删除这些用户。

## 相关阅读

* 在Commerce on cloud infrastructure指南中[查看用户的项目角色](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html#view-a-user的project-role)。
* [如何在Commerce KB的支持通知中包含团队成员](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-include-a-team-member-in-support-notifications.html)。
