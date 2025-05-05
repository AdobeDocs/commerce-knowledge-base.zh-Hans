---
title: 与帐户权限和访问密钥相关的部署问题
description: 本文为因访问密钥所有权冲突导致的在云基础架构上部署Adobe Commerce时出现的问题提供了解决方案。
exl-id: e8d72ebe-453f-4d18-a25e-c76e685aa667
feature: Deploy, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 与帐户权限和访问密钥相关的部署问题

本文为因访问密钥所有权冲突导致的在云基础架构上部署Adobe Commerce时出现的问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有受支持的版本

## 问题

<u>先决条件</u>：

云许可证与联系人A关联(电子邮件地址： *<u>first@e.mail</u>*)

<u>重现步骤</u>：

1. 联系在其帐户中创建的Adobe Commerce访问密钥（密钥X），并将其安装在云中。
1. 联系人B(电子邮件地址：*<u>second@e.mail</u>*)使用其帐户购买了一个扩展，并创建了用于安装该扩展的访问密钥（密钥Y）。
1. 联系人A随后离开了公司，许可证（所有权）随后转让给联系人B。
1. 系统集成商尝试使用密钥X在云环境中安装扩展。

<u>预期的结果</u>：

已成功安装扩展。

<u>实际结果</u>：

未安装扩展，因为部署失败。

## 原因

这两个键都被分配给联系人角色，这会导致冲突。

## 解决方案

如果对帐户上的主要联系人进行更改后部署失败（原始帐户和新帐户各自都有自己的访问密钥），并且密钥已从原始帐户转移到新帐户，则需要禁用原始帐户的密钥。 根据上面的示例，应该禁用键X。

### 如何禁用访问密钥

如果您无权访问与旧密钥关联的[Commerce Marketplace](https://marketplace.magento.com/)帐户，请[联系Adobe Commerce支持部门](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以禁用该密钥。

如果您有权访问与旧密钥关联的Marketplace帐户，请执行以下步骤来禁用该密钥：

1. 使用旧帐户的凭据登录到[Commerce Marketplace](https://marketplace.magento.com/)。
1. 单击页面右上角的帐户名称，然后选择&#x200B;**我的个人资料**。
1. 在“市场”选项卡中单击&#x200B;**访问密钥**。

   ![magento_products_access_keys_2.4.1.png](/help/troubleshooting/miscellaneous/assets/magento_products_access_keys_2.4.1.png)

1. 单击访问密钥旁边的&#x200B;**禁用**。

## 相关阅读

* [在我们的开发人员文档中获取您的身份验证密钥](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/authentication-keys)。
