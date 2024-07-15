---
title: '云上的Adobe Commerce：更改身份验证密钥并重新部署'
description: 本文提供了有关如何使用不同的身份验证密钥在云基础架构上重新部署Adobe Commerce的说明。 例如，您可能使用了其他帐户的密钥，或者使用的是Magento Open Source密钥而不是Adobe Commerce密钥。
exl-id: 47407c81-5c52-406f-812f-6c6b3ca5cafa
feature: Cloud, Deploy
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 云上的Adobe Commerce：更改身份验证密钥并重新部署

本文提供了有关如何使用不同的身份验证密钥在云基础架构上重新部署Adobe Commerce的说明。 例如，您可能使用了其他帐户的密钥，或者使用的是Magento Open Source密钥而不是Adobe Commerce密钥。

如果您使用的密钥不正确，则部署失败。 要恢复，您必须克隆项目，将正确的密钥添加到`auth.json`，并将更改推送到主分支。

在本文中，我们假定您的项目仅具有`master`分支（`master`是您首次创建项目时的默认分支）。

使用正确的身份验证密钥重新部署：

1. 登录到拥有Adobe Commerce on cloud infrastructure SSH密钥的计算机。
1. 登录项目：

   ```
   magento-cloud login
   ```

1. 创建分支以更新名称为`auth`的代码：

   ```
   magento-cloud environment:branch auth master
   ```

1. 更改为项目根目录。
1. 在文本编辑器中打开`auth.json`。

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. 添加正确的身份验证密钥。
1. 保存更改并退出文本编辑器。
1. 提交并合并更改。

   ```
   git add -A
   ```

   ```
   git commit -m "<description of change>"
   ```

   ```
   git push origin master
   ```

1. 等待部署完成。

消息指示部署是否成功。 您可以通过转到屏幕上显示的&#x200B;**环境路由**&#x200B;之一来确认部署成功。
