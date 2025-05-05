---
title: 未验证PayPal沙盒帐户
description: 本文解释了为什么无法验证您用于支付服务的PayPal沙盒帐户，从而阻止您完成沙盒载入。
exl-id: 05ce130d-6dfe-4834-bdfc-837902100118
feature: Customer Service, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 未验证PayPal沙盒帐户

本文解释了为什么无法验证您用于支付服务的PayPal沙盒帐户，从而阻止您完成沙盒载入。

## 受影响的产品和版本

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html)现在与Adobe Commerce版本2.4.0到2.4.4兼容。

## 问题

我们的[入门文档](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html?lang=zh-Hans)指示您注册PayPal帐户，登录PayPal开发人员帐户，然后创建沙盒帐户。 如果您选择在新用户引导期间在PayPal新用户引导弹出窗口中创建新帐户，PayPal将无法验证您的沙盒帐户，并且您将无法完成新用户引导。

<u>重现步骤</u>：

1. 您[安装付款服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html?lang=zh-Hans)并[配置您的Commerce服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html?lang=zh-Hans#configure-commerce-services)。
1. 在管理员中导航到&#x200B;**付款服务**，然后[启动沙盒载入](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/onboard.html?lang=zh-Hans)。
1. 在出现的PayPal登录弹出窗口中，您创建一个新的企业帐户（而不是[在登录期间使用之前创建的PayPal沙盒帐户](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html?lang=zh-Hans#test-in-sandbox-environment)登录）。
1. 您已成功完成PayPal入门。
1. 您会在管理员中看到一则通知，表明您的沙盒支付正在等待处理，您必须通过PayPal确认您的电子邮件地址才能完成入门。

   您未收到确认电子邮件，因为PayPal无法验证您的电子邮件地址。

## 原因

如果您在PayPal帐户之前创建沙盒帐户，PayPal将无法验证您的沙盒帐户，并且您将无法完成沙盒载入（这意味着您无法接受付款或测试沙盒模式）。

## 解决方案

1. 使用在[PayPal开发人员](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account)门户中创建的沙盒帐户。
1. 单击[重置沙盒](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html?lang=zh-Hans#test-in-sandbox-environment)，然后重新启动沙盒载入。
1. 如果无法缓解帐户问题，请[联系支持人员](mailto:payment-services-support@adobe.com)，以便您可以继续登录并接受付款。
