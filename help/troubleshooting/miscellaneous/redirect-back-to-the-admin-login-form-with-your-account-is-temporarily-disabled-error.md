---
title: 重定向回Commerce管理员登录表单，其中显示“您的帐户暂时被禁用”错误
description: '''本文为Commerce管理员登录问题提供了可能的解决方案，在该问题中，您将被重定向回登录表单，并出现以下错误消息：*“您的帐户已被暂时禁用”*。 建议的解决方案是检查并更正管理员用户数据库设置。'
exl-id: 1c7ffa1c-1fb1-4f69-9534-77d1e119318a
feature: Admin Workspace, Customer Service
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# 重定向回Commerce管理员登录表单，其中显示“您的帐户暂时被禁用”错误

本文为Commerce管理员登录问题提供了可能的解决方案，您会在该问题中被重定向回登录表单，并显示以下错误消息： *“您的帐户已被暂时禁用”*. 建议的解决方案是检查和更正管理员用户数据库设置。

## 受影响的版本和版本：

所有Adobe Commerce版本和版本

## 问题

<u>重现问题的步骤</u>：

1. 转到Commerce管理页面。
1. 输入您的凭据，然后单击“登录”。

<u>预期结果</u>：

您将登录到Commerce管理员。

<u>实际结果</u>：

系统会将您重定向回登录表单，并显示以下错误消息： *“您的帐户已暂时禁用。 请稍后重试”*.

## 解决方案

1. 创建数据库备份。
1. 使用数据库工具，例如 [phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)，或从命令行手动访问数据库。 在 `admin_user` 数据库表，对于管理员用户记录，检查 `is_active` 设置为&quot;`1`”和 `lock_expires` 是 `NULL`. 如果需要，请重置这些值。

## 我们的支持知识库中的相关阅读

* [尝试登录Commerce管理员时，重定向回登录表单，并且未出现错误](/help/troubleshooting/miscellaneous/login-redirect-when-trying-to-login-to-magento-admin.md)
