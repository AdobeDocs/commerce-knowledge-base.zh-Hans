---
title: '无法访问云存储库上的Adobe Commerce：部署时出现403 Forbidden或404 Not Found错误'
description: '本文讨论如何解决云基础架构上的Adobe Commerce部署失败错误，错误类似于以下内容：'
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# 无法访问云存储库上的Adobe Commerce：部署时出现403 Forbidden或404 Not Found错误

本文讨论如何解决云基础架构上的Adobe Commerce部署失败错误，错误类似于以下内容：

“*无法访问&#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL： HTTP/1.1 403 Forbidden* ”。 或无法下载“*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip”文件（HTTP/1.1 404未找到）*”。

## 受影响的产品和版本

* 云基础架构2.2.x、2.3.x和2.4.x上的Adobe Commerce

## 问题

部署上的错误消息，指示无法访问存储库URL。

<u>重现步骤</u>

手动触发部署，或通过执行环境的合并、推送或同步来触发部署。

<u>实际结果</u>

部署卡住。 在项目UI的部署错误日志中，会显示类似于以下内容的错误消息：

*“无法访问&#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; URL： HTTP/1.1 \[403 Forbidden or 404 Not Found\]”*。

（单击项目UI中的“失败”图标可查看日志。）

<u>预期的结果</u>

已成功完成部署。

## 原因

该错误是由授权密钥（访问密钥）无效、未指定或未正确指定造成的。

密钥无效的部分原因包括：

* 您使用共享帐户生成了密钥。
* 由于付款问题，您的许可证以前已被吊销。

>[!NOTE]
>
>如果您发现这是由于开票或合同问题而引起，请联系您的Adobe客户团队以获取解决此问题的指导。 重新激活许可证后，将恢复您的支持和部署授权。

## 解决方案

执行以下步骤来解决授权密钥的问题（有关每个步骤的更多详细信息，请参阅以下部分）：

1. 获取有效的授权密钥（如果绝对确定您的密钥有效，请跳过此步骤）。
1. 在`env:COMPOSER_AUTH`变量中添加键值（或确保存在正确的值），并检查在项目级别和环境级别的变量中以及在项目根目录中的`auth.json`文件（如果存在）中是否以一致的方式指定键。
1. 如果未指定授权密钥值或具有其他值，请更新或删除`auth.json`，以便在单个位置配置密钥。

### 1.获取有效的授权密钥

如果您使用在共享帐户下创建的密钥，则需要联系Adobe Commerce许可证所有者，该所有者为您提供访问权限并请求他们为您生成密钥。

如果您的许可证先前因付款问题而被撤销，并且您已解决这些问题并且已续订许可证，则您需要[生成新的身份验证密钥](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=zh-Hans)。

### 2.在env：COMPOSER\_AUTH变量中添加键值，并检查是否在auth.json中指定了相同的键

请参阅我们的开发人员文档中的[准备现有系统](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/project/overview)和[添加身份验证密钥](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/project/overview)中的说明和相关信息。

### 3.更新或删除auth.json

以下分步说明如何更新授权密钥：

1. 登录到拥有Adobe Commerce on cloud infrastructure SSH密钥的计算机。
1. 登录项目： `magento-cloud login`
1. 创建分支以更新代码（在以下示例中，从主分支创建的分支名称为`auth`）：     `magento-cloud environment:branch auth master`
1. 更改为项目根目录。
1. 可选：如果您愿意，请删除`auth.json`并继续执行[步骤9](#step9)。
1. 在文本编辑器中打开`auth.json`。

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. 添加正确的身份验证密钥。
1. 保存更改并退出文本编辑器。
1. 提交并合并更改：

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. 等待项目部署。
