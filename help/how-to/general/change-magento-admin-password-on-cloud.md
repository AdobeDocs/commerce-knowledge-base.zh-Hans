---
title: 在云基础架构上更改Adobe Commerce上的管理员密码
description: ！[login_panel_s.png](assets/login_panel_s.png)
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 44238f6d57458028cb1e2612d45e1e12b3f39916
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# 在云基础架构上更改Adobe Commerce上的管理员密码

## 方法1：忘记密码（通过电子邮件重置）

![login_panel_s.png](assets/login_panel_s.png)

阅读我们的用户指南中“管理员登录”[&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html?lang=zh-Hans#admin-sign-in)的重置密码一节中的步骤。

以下是关键使用说明。

### 启用传出电子邮件

在使用&#x200B;**忘记密码**&#x200B;表单之前，请确保使用[云控制台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hans)启用传出电子邮件[&#128279;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html?lang=zh-Hans)。 这仅适用于集成环境和沙盒项目。

如果在Pro Production或Staging上确实禁用了传出电子邮件（即SendGrid未提取电子邮件），则可以通过选中[在Cloud Console中启用电子邮件](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/project/outgoing-emails#enable-emails-in-the-cli)来验证此设置。 如果问题仍然存在，您可以提交Adobe [支持票证](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)。

### 检查您的“垃圾邮件”文件夹

如果“重置密码”链接找不到邮件，请检查你的&#x200B;*垃圾邮件*&#x200B;文件夹。 电子邮件的名称为&#x200B;*管理员用户名*&#x200B;的密码重置确认。

## 方法2：添加新的管理员用户

如果无法恢复或重置现有用户的密码，则可以创建新的管理员用户并设置此用户的密码。 为此，请执行以下步骤：

1. 使用[SSH登录到远程环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans)。
1. 运行以下命令： `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
