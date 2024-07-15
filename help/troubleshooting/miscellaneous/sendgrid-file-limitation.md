---
title: '[!DNL SendGrid] Adobe Commerce Cloud文件限制'
description: 本文为Adobe Commerce在云基础架构上的 [!DNL SendGrid] 限制提供了解决方法。
feature: Deploy, Marketing Tools
role: Developer, Admin
exl-id: 48629f48-8100-4128-9211-53d947aecd49
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Adobe Commerce Cloud的[!DNL SendGrid]限制

本文为Adobe Commerce在云基础架构上的[!DNL SendGrid]限制提供了一些解决方法。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)


## 问题

您尝试在电子邮件中发送大型附件，并看到以下日志错误：

在`/var/log/mail.log`

```shell
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[21408]: fatal: no-reply@xxxxxxxx.com(8080): message file too big
Month Date Time i-xxxxxxxxxxxxxxxxx postfix/sendmail[26434]: fatal: no-reply@xxxxxxxxx.com(8080): message file too big
```

在`/var/log/exception.log`

生产：

`/app/<project-id>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

暂存：

`/app/<project-id_stg>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

暂存2：

`/app/<project-id_stg2>/vendor/laminas/laminas-mail/src/Transport/Sendmail.php:313`

## 原因

[!DNL SendGrid]的系统限制为电子邮件30Mb大小。 建议不要使用超过10Mb的附件。 有关详细信息，请参阅SendGrid文档中的[发送附件](https://docs.sendgrid.com/ui/sending-email/attachments-with-digioh)。

## 解决方法

* 请勿使用大于6Mb或10Mb的附件。
* 考虑在Adobe Commerce实例上使用远程SMTP服务器。 有关步骤，请参阅我们的管理员系统指南中的[配置电子邮件通信](https://experienceleague.adobe.com/docs/commerce-admin/systems/communications/email-communications.html)。
* 重新配置服务器，以便在模块中保存文件，然后将链接附加到电子邮件中的文件。

## 相关阅读

* 我们的Commerce on Cloud Infrastructure指南中的[[!DNL SendGrid] 电子邮件服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html)。
