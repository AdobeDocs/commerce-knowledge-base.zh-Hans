---
title: PayPal Payflow主动分卡活动
description: 2019年4月2日更新
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# PayPal Payflow主动分卡活动

2019年4月2日更新

Adobe Commerce的PayPal Payflow Pro集成正成为读卡活动的积极目标，攻击者试图利用被盗信用卡进行数百美元交易，以检查信用卡的有效性。

本活动当前定位的是此Payflow Pro集成的版本，这些版本包括在Adobe Commerce 2.1.x、2.2.x、2.3.x的Magento Open Source和Commerce（内部部署和云）中。 梳理活动是Payflow Pro集成到购物车中的固有方式。

>[!NOTE]
>
>为了帮助解决这些问题，我们提供了新的Composer包，以将Google reCAPTCHA或CAPTCHA添加到Payflow Pro结账表单中。 我们建议在所有Adobe Commerce版本上安装这些软件包。

该问题会影响以下Adobe Commerce版本：

* Adobe Commerce内部部署v2.1.x、2.2.x、2.3.x
* 云基础架构上的Adobe Commerce v2.1.x、2.2.x、2.3.x

## 问题

这些攻击的症状包括：

* 您的PayPal Payflow Pro帐户显示已识别的数百个欺诈交易
* PayPal可能会因传入的欺诈交易而暂停Payflow Pro帐户，并收取大笔费用

## 解决方案

为了帮助防御这些攻击，我们建议将Google reCAPTCHA（推荐）或CAPTCHA添加到Payflow Pro结账表单中。 这包括安装编辑器包，以及在Commerce管理员中配置Google reCAPTCHA或CAPTCHA。

### 安装包

Adobe创建了两个包选项，用于将Google reCAPTCHA和/或CAPTCHA添加到Payflow Pro结账表单中。 安装其中一个软件包将更新当前安装，并向Payflow Pro签出表单添加一个有助于增强此安全性的选项。

这些包与以下Adobe Commerce部署和版本兼容：

Adobe Commerce（所有部署方法）和Magento Open Source2.1.x、2.2.x、2.3.x

安装时需要Adobe Commerce实例使用CLI命令。 可能需要开发人员协助。

>[!NOTE]
>
>除了安装任何相关的Payflow Pro签出表单更新外，我们建议安装和配置Google reCAPTCHA。 此选项提供不可见的检查和多个配置选项。

#### 安装Google reCAPTCHA并签出表单更新

`magento/module-paypal-recaptcha`包包含与Google reCAPTCHA和Payflow Pro支付表单更新的集成。 即使您已安装和配置reCAPTCHA模块，我们仍建议您安装此包。

运行以下命令进行安装。

针对Adobe Commerce本地：**&#x200B;**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

云基础架构上的Adobe Commerce的&#x200B;**：**

1. 运行以下命令：

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. 提交和推送更改：

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. 等待部署完成。

#### 安装验证码的签出表单更新

`magento/module-paypal-captcha`包包含与本机Adobe Commerce CAPTCHA模块的集成。

运行以下命令进行安装：

针对Adobe Commerce本地：**&#x200B;**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

云基础架构上的Adobe Commerce的&#x200B;**：**

1. 运行以下命令：

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. 提交和推送更改：

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. 等待部署完成。

### 配置Google reCAPTCHA或CAPTCHA

安装包后，请按照以下文档中的说明配置Google reCAPTCHA（推荐）或CAPTCHA：

* 用户指南中的[Google reCAPTCHA](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/captcha/security-google-recaptcha)。
* 用户指南中的[验证码](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/captcha/security-captcha)。

新的签出表单选项为：

* Google reCAPTCHA：用于PayPal Payflow Pro支付表单
* 验证码：Payflow Pro

## PayPal支持和联系人

请联系PayPal Payflow商家支持以了解有关欺诈防护服务的更多信息。 您可以请求PayPal支持团队启用[基本欺诈保护服务](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/)过滤器，以对付款提供尽可能严格的控制功能，以便您可以自动拒绝可能导致欺诈交易的付款，并接受通常不会成为问题的付款。 请注意，启用PayPal欺诈防护服务过滤器后，交易可能需要长达2小时才能结算。

>[!NOTE]
>
>有关其他信息，请参阅PayPal知识库[“Adobe已就我的Payflow Pro集成与我联系。 我需要做什么？&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**PayPal Payflow商家支持详细信息**

Payflow商家支持的营业时间为星期一至星期五上午7:00 - 8:00（中部标准时间）。 您可以通过电话或电子邮件联系Payflow商家支持以获取帐户帮助：

* 电话： 1-888-883-9770 （选择提示2）
* 国际客户：1-408-967-0191
* 电子邮件： [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

澳大利亚支持

* 星期一至星期五上午8:00 — 晚上7:00 （AU时间）
* 电话： +61 2 8288 0198
* 电子邮件： [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
