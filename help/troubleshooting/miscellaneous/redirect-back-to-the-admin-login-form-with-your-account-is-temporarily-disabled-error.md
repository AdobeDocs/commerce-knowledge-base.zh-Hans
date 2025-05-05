---
title: '重定向回[!UICONTROL Commerce Admin]登录表单，并显示“您的帐户暂时被禁用”错误'
description: '''本文为Commerce管理员登录问题提供了可能的解决方案，在该问题中，您将被重定向回登录表单，并出现以下错误消息：*“您的帐户已被暂时禁用”*。 建议的解决方案是检查并更正管理员用户数据库设置。'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# 重定向回[!UICONTROL Commerce Admin]登录表单，并显示“您的帐户暂时被禁用”错误

本文为[!UICONTROL Commerce Admin]登录问题提供了可能的解决方案，在该问题中，您将被重定向回登录表单，并出现以下错误消息： *“您的帐户被暂时禁用”*。 建议的解决方案是检查和更正管理员用户数据库设置。

## 受影响的版本和版本：

所有Adobe Commerce版本和版本

## 问题

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Commerce Admin]**&#x200B;页面。
1. 输入您的凭据，然后单击&#x200B;**登录**。

<u>预期的结果</u>：

您已登录[!UICONTROL Commerce Admin]。

<u>实际结果</u>：

您将被重定向回登录表单，并显示以下错误消息： *&quot;您的帐户已暂时禁用。 请稍后重试“*”。

## 解决方案

1. 创建数据库备份。
1. 使用数据库工具，如[[!DNL phpMyAdmin]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)，或从命令行手动访问数据库。 在`admin_user`数据库表中，对于管理员用户记录，检查`is_active`是否设置为“`1`”，`lock_expires`是否为`NULL`。 如果需要，请重置这些值。

## 相关阅读

* [尝试登录到[!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)时，重定向回登录表单，没有错误
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
