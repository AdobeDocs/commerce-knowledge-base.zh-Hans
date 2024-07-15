---
title: “[!DNL Admin]登录不起作用 — 超出了允许的会话最大大小”
description: 解决当您尝试登录 [!DNL Admin] 面板并且表单刷新且无法登录的问题。
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin]登录不起作用 — 超出了允许的会话最大大小

本文修复了以下问题：当您尝试登录[!DNL Admin]面板时，表单刚刚刷新，无法登录。 这是因为已超出[!DNL Admin]会话大小。

## 受影响的版本

* Adobe Commerce内部部署，[所有支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 云基础架构上的Adobe Commerce，[所有支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

无法登录到[!DNL Admin]，因为表单不断重新加载。

## 原因

超出了允许的会话最大大小。

## 解决方案

检查`var/log/support_report.log`文件中是否存在错误，例如：

*[2023-07-13T04:26:09.792060+00:00]报告。警告： 260572的会话大小超过了允许的会话最大大小256000。 [] []
[2023-07-13T04:26:17.056714+00:00]报告。警告： 260570的会话大小超过了允许的会话最大大小256000。[][]*

如果您看到这些错误，解决办法将是：

<u>Adobe Commerce内部部署</u>：
1. 从后端配置增加&#x200B;**[!UICONTROL Max Session Size in Admin]**&#x200B;值。 为此，请转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**。
1. 将该值设置为&#x200B;*500000*&#x200B;或更高。 根据错误中报告的现有最大大小 — 您还可以将该值设置为&#x200B;*0*，这将删除会话大小限制。

云基础架构上的<u>Adobe Commerce</u>：

(仅当部署/操作模式为默认或开发人员时，此设置只能在[!DNL Admin]中访问。 但是，在云环境中只允许使用生产部署模式。)

要增加此值，请在终端(SSH)中运行此命令：

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

您可以将设置为大于&#x200B;*500000*，具体取决于错误中报告的现有最大大小，您还可以将值设置为&#x200B;*0*&#x200B;以移除会话大小限制。

## 相关阅读

* 管理系统指南中的[会话大小](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions)。
* 配置指南中的[操作模式](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode)。
* 云基础架构上的Commerce指南中的[安全连接](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections)。
