---
title: 管理员密码以纯文本形式保存到操作日志
description: 本文修复了以下问题：Commerce管理员创建具有管理员权限的新用户，且密码保存为“magento_logging_event_changes”数据库表中的纯文本。
exl-id: 0e91198e-66b9-456a-9b75-5986369ed8e6
feature: Admin Workspace, Logs
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 管理员密码以纯文本形式保存到操作日志

本文修复了以下问题：Commerce管理员如何创建具有管理员权限的新用户，并且密码在中保存为纯文本。 `magento_logging_event_changes` 数据库表。

要修复此安全问题，请安装Adobe Commerce 2.0.16和2.1.9安全更新。 应用安全更新后，密码将加密，不会显示为纯文本。

## 受影响的版本 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Affectedversions}

* Adobe Commerce内部部署2.X.X
* 云基础架构上的Adobe Commerce 2.X.X

## 问题 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Issue}

当现有Commerce管理员通过创建具有管理员权限的新用户时 **系统** > **权限** > **所有用户** > **添加新用户**，密码（作为确认输入）将作为纯文本保存在中 `magento_logging_event_changes` 数据库表。

### 重现问题的步骤： {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Stepstoreproduce}

1. 以管理员身份登录，并通过导航到以下路径创建新用户： **系统** >权限> **所有用户**.

   ![add_user_magento_2.4.1.png](assets/add_user_magento_2.4.1.png)

1. 然后单击 **添加新用户** 页面。 提示时提供当前管理员的密码。
1. 转到 **系统** > **操作日志** > **报表** 页并查找最后一个日志条目。
1. 您可以查看当前密码，该密码既未加密，也未经过哈希处理。

## 解决方案 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Solution}

安装 [Adobe Commerce 2.0.16和2.1.9安全更新](https://magento.com/security/patches/magento-2016-and-219-security-update) 修复了此问题。

安装安全更新后，密码将进行加密，并且不会以纯文本形式显示在 `magento_logging_event_changes` 表格。

## 更多信息 {#Adminpasswordsaresavedasplaintexttoactionslog('magento_logging_event_changes'table)-Moreinformation}

[Adobe Commerce 2.0.16和2.1.9安全更新页面](https://magento.com/security/patches/magento-2016-and-219-security-update) 在我们的安全中心。

[升级Adobe Commerce应用程序和组件](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) 在我们的开发人员文档中。
