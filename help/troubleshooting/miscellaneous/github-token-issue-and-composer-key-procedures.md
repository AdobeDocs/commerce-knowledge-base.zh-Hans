---
title: Github令牌问题和编辑器密钥过程
description: 本文提供了与Github令牌失败相关的部署失败问题的解决方案，这些失败是由过期的编辑器密钥导致的。
exl-id: 202cb936-f9ba-49ea-bf0a-6e6994d2337a
feature: Identity Management
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Github令牌问题和编辑器密钥过程

本文提供了与Github令牌失败相关的部署失败问题的解决方案，这些失败是由过期的编辑器密钥导致的。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* Composer版本1.10.20及更低版本

>[!NOTE]
>
>由于Git引入的令牌格式更改，Adobe Commerce本地商家应当与其主机提供商确认，以确保他们使用的是Composer版本1.10.21或更高版本。

## 问题

部署失败，部署日志包含与以下内容类似的信息：

*致命错误：未捕获的UnexpectedValueException：您的github.com的github oauth令牌包含无效字符： /app/vendor/composer/composer/src/Composer/IO/BaseIO.php:129*&#x200B;中的“ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx”

## 原因

编辑器密钥过期会导致Github令牌失败，进而导致部署失败。

## 解决方案

要解决此问题，请将您的编辑器版本更新为1.10.22：

1. 在本地环境中，运行`composer require “composer/composer”:”>1.10.21`。
1. 这添加了对该编辑器包版本的要求。 检查锁定文件 — `composer/composer`版本必须为1.0.22或更高版本。
1. 提交`composer.json`和`composer.lock`并推送部署。

如果此方法不起作用，请[提交支持票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)。

## 相关阅读

* [Github博客：在GitHub的新身份验证令牌格式之后](https://github.blog/2021-04-05-behind-githubs-new-authentication-token-formats/)
* [InfoQ.com新闻文章： GitHub更改令牌格式以提高可识别性、密钥扫描和熵](https://www.infoq.com/news/2021/04/github-new-token-format/)
