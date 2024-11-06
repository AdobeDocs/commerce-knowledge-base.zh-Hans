---
title: 尝试登录Commerce Admin时的登录重定向
description: 本文为Commerce管理员登录问题提供了可能的解决方案，在该问题中，当您尝试登录到管理员时，会被重定向回登录表单，并且不会显示错误消息。 这包括更正服务器时区设置和清除Adobe Commerce中的Cookie设置。
exl-id: ff3114fd-8690-4983-8221-cf807f083b15
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# 尝试登录Commerce Admin时的登录重定向

本文为Commerce管理员登录问题提供了可能的解决方案，在该问题中，当您尝试登录到管理员时，会被重定向回登录表单，并且不会显示错误消息。 这包括更正服务器时区设置和清除Adobe Commerce中的Cookie设置。

## 受影响的版本和版本：

所有Adobe Commerce版本和版本。

## 问题

<u>重现步骤</u>：

1. 转到您的Commerce管理页面。
1. 输入您的凭据，然后单击“登录”。

<u>预期的结果</u>：

您将登录到Commerce管理员。

<u>实际结果</u>：

系统会将您重定向回登录表单，且不会显示任何错误消息。

## 原因

导致此问题的可能原因有两个：

* 在浏览器级别设置的时区不正确（这会导致管理员会话被视为已过期，即使其实际生命周期尚未过期）。
* Cookie设置不正确，这会导致Adobe Commerce不使用已建立的会话。

对于每种情况的解决方案，请参阅下面的各段。

## 解决方案

### 管理员会话生命周期问题

尝试使用其他浏览器，如果不足1小时，则延长管理会话生命周期。

要延长管理会话的生命周期，请执行以下步骤：

1. 创建数据库备份。
1. 使用数据库工具（如[phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)），或者从命令行手动访问数据库以运行以下SQL查询：

   ```sql
   UPDATE core_config_data SET value = 7200 WHERE path = 'admin/security/session_lifetime';
   ```

1. 通过运行以下命令清除配置缓存：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

### Cookie设置不正确

要检查Cookie设置值并清除它们，请执行以下步骤：

1. 创建数据库备份。
1. 使用数据库工具（如[phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)），或者从命令行手动访问数据库以运行以下SQL查询：

   ```sql
   SELECT * FROM core_config_data WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. 如果值的响应不为空，请通过运行以下命令将其设置为NULL：

   ```sql
   UPDATE core_config_data SET value = NULL WHERE (path = "web/cookie/cookie_domain" OR path = "web/cookie/cookie_path");
   ```

1. 通过运行以下命令清除配置缓存：

   ```bash
   php <your_magento_install_dir>/bin/magento cache:clean config
   ```

## 相关文章

* [重定向回管理员登录表单，在我们的支持知识库中出现“您的帐户已被暂时禁用”错误](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-account-is-temporarily-disabled-error.md)。
* [重定向回管理员登录表单，在我们的支持知识库中出现“您的当前会话已过期”错误](/help/troubleshooting/miscellaneous/redirect-back-to-the-admin-login-form-with-your-current-session-has-been-expired-error.md)。
