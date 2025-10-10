---
title: 未收到管理员2FA电子邮件通知
description: 本文介绍了在设置了双重身份验证(2FA)以增强Adobe Commerce中云基础架构上的管理员访问安全后，如果在收到带有设置完成说明的电子邮件时无法进行故障排除。
exl-id: 7ab6b2b4-6aca-4323-a45b-2b4e52955160
feature: Admin Workspace, Communications
role: Developer
source-git-commit: 9eaea028886e74fc06c9516801919cd7f650f98c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 未收到管理员2FA电子邮件通知


## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

您已设置双重身份验证以增强管理员访问安全性，但没有收到包含完成设置说明的电子邮件。

## 原因

如果您未正确配置发件人电子邮件，或者您的域未在SendGrid中标为白标，则电子邮件很可能最终位于“垃圾邮件”文件夹中。

## 故障排除

### 步骤1：检查垃圾邮件文件夹

1. 如果电子邮件未出现在Spam文件夹中，请运行此Mysql查询以验证电子邮件地址是否已配置：

   ```sql
   select * from core_config_data where path like '%trans_email%';
   ```

   * 如果未返回任何结果，则表示尚未配置发件人地址。
由于您无权访问管理员，因此必须将配置插入数据库。 插入相应的电子邮件地址并运行MySQL语句：

   ```
   insert into core_config_data (scope,scope_id,path,value) values ('default',0,'trans_email/ident_general/email', your-email@here.com)
   ```

   * 如果返回结果，则继续执行&#x200B;**步骤2**。

1. 如果电子邮件出现在您的“垃圾邮件”文件夹中，请单击电子邮件中的链接。 如果该链接已过期，请尝试再次登录以重复该过程。
1. 获得访问权限后，请转到&#x200B;**商店** > **配置** > **常规** > **商店电子邮件地址**&#x200B;并配置电子邮件地址。

### 步骤2：如果正确配置了电子邮件地址/一旦配置了电子邮件地址，请SSH进入环境并运行此命令：

```php
php -r "mail(<your email address>,<subject>,<content>,'To: <sender email>');"
```

检查您的Spam文件夹中的电子邮件。

如果电子邮件出现在您的“垃圾邮件”文件夹中，则域的电子邮件身份验证可能未完全配置为通过SendGrid出站投放。

如果您使用由Adobe管理的SendGrid服务：

[提交支持票证](https://experienceleague.adobe.com/home?support-tab=home#support)，请求使用SendGrid对您的发送域进行身份验证（有时称为&#x200B;*白标签*）。
此过程包括添加DNS记录(DKIM和SPF)以授权SendGrid代表您的域发送电子邮件，这会增加将您的电子邮件投放到收件箱而不是Spam文件夹的可能性。

如果您使用自己的SendGrid帐户：

您负责直接在SendGrid帐户仪表板中管理域身份验证设置。 有关详细信息，请参阅SendGrid文档中的[如何设置域身份验证](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/how-to-set-up-domain-authentication)。

>[!NOTE]
>
>某些客户可能会选择使用单独配置的SendGrid服务，以便完全控制电子邮件的可投放性和合规性（例如HIPAA要求）。 根据您使用的SendGrid服务类型(Adobe托管与自托管)，确保遵循正确的故障排除步骤。


## 相关阅读

* 在我们的开发人员文档中[SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid)。
