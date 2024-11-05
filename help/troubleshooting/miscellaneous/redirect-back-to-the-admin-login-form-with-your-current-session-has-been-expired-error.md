---
title: '重定向回[!UICONTROL Commerce Admin]登录表单，其中显示“您的当前会话已过期”错误'
description: '''本文提供了[!UICONTROL Commerce Admin]登录问题的可能解决方案，您会在该问题中被重定向回登录表单，并出现以下错误消息：*“您的当前会话已过期”*。 解决方案包括检查服务器时间设置问题和更改会话存储设置。'
exl-id: 29df2ed2-ff4a-4f1a-bdb7-1160416cda00
feature: Admin Workspace
role: Developer
source-git-commit: 3f205b1d755bda7056f47bf1e1d036feb47ebadd
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 重定向回[!UICONTROL Commerce Admin]登录表单，其中显示“您的当前会话已过期”错误

本文为[!UICONTROL Commerce Admin]登录问题提供了可能的解决方案，在该问题中，您将被重定向回登录表单，并出现以下错误消息： *“您的当前会话已过期”*。 解决方案包括检查服务器时间设置问题和更改会话存储设置。

## 受影响的版本和版本：

所有Adobe Commerce版本和版本

## 问题

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Commerce Admin]**&#x200B;页面。
1. 输入您的凭据，然后单击&#x200B;**登录**。

<u>预期的结果</u>：

您已登录[!UICONTROL Commerce Admin]。

<u>实际结果</u>：

您将被重定向回登录表单，并显示以下错误消息： *“您的当前会话已过期”*。

## 原因

这个问题可能有两个原因：

* 服务器时间设置问题
* 会话存储问题

请查看以下部分以了解解决方案。

## 解决方案

### 检查服务器时间设置问题

检查`admin_user_session`表中创建的会话记录。 如果`created_at`和/或`updated_at`的值不正确，则可能是由于服务器时间设置问题造成的。 请要求您的服务器系统管理员检查这一点。 请注意，默认情况下，DB中的时间设置为UTC。

### 更改会话存储

尝试更改会话存储。 使用我们的开发人员文档中的[如何找到您的会话文件](https://devdocs.magento.com/guides/v2.3/config-guide/sessions.html)文章中的信息来查找您的会话存储的位置，并通过编辑`app/etc/env.php`文件来更改它。

例如，要在文件系统中开始存储会话，请按以下方式更改`'session'`部分：

```php
....
'session' =>
    array (
      'save' => 'files',
),
....
```

运行`bin/magento app:config:import`命令以导入配置数据。


## 相关阅读

* 从开发人员文档中的配置文件[导入数据](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-config-mgmt-import.html)
* 在开发人员文档中[配置 [!DNL Redis]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/redis/config-redis)
* [重定向回[!UICONTROL Commerce Admin]登录表单，并在我们的支持知识库中出现“您的帐户被暂时禁用”错误](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error)
* [尝试登录到我们的支持知识库中的[!UICONTROL Commerce Admin]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin)时，重定向回登录表单且没有错误
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

