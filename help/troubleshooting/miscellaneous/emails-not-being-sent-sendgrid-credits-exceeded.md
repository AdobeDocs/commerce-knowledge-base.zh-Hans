---
title: 在Adobe Commerce上超过SendGrid信用时未发送电子邮件
description: 当您的电子邮件因超出Adobe Commerce上的SendGrid信用限制而未发送时，本文提供了一个解决方案。
exl-id: 43438890-665b-4408-8034-e61de8fbbd8b
feature: Communications, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 在Adobe Commerce上超过SendGrid信用时未发送电子邮件

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.0 - 2.3.7-p1， 2.4.0 - 2.4.3

## 问题

SendGrid信用指可以发送的允许电子邮件数。 每月从集成和暂存分支只能发送12,000封电子邮件。 积分将在月初续订，因此，如果您没有足够的积分，则必须等待续订。

只要发件人信誉超过95%，生产环境中可以发送的电子邮件数量就没有任何硬性限制。 信誉受退回/拒绝的电子邮件数量以及基于DNS的垃圾邮件注册是否已将您的域标记为潜在垃圾邮件来源的影响。 在生产环境中，每天会分配总计12,000封电子邮件，但可以根据前五天内发送的平均电子邮件数扩展该数量。

## 如何检查您的积分是否超出：

云基础架构上的Adobe Commerce Pro计划架构：检查`/var/log/mail.log` — 您可能会看到如下消息：

`May 28 21:13:00 <i-node> postfix/error[21335]: BC7941A2BBF: to=<to@email.com>, relay=none, delay=4642, delays=4642/0.56/0/0.03, dsn=4.0.0, status=deferred (delivery temporarily suspended: SASL authentication failed; server smtp.sendgrid.net[ip address] said: 451 Authentication failed: Maximum credits exceeded).`

## 原因

允许发送的电子邮件数量存在限制。

## 解决方案

* 如果您在生产环境中看到此消息，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)并提供上述消息并请求增加积分。
* 如果您没有看到此消息，或者您在云基础架构入门计划架构上的Adobe Commerce上，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，并提及`mail.log`文件未指示信用额度已超出。

## 相关阅读

* 在我们的开发人员文档中[SendGrid](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/sendgrid)。
