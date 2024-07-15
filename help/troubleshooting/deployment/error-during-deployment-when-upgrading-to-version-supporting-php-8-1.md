---
title: 升级到支持PHP 8.1的版本时，在部署过程中出错
description: 本文提供了在升级到支持PHP 8.1的版本时部署过程中发生的错误的解决方案。
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# 升级到支持PHP 8.1的版本时，在部署过程中出错

本文提供了在升级到支持PHP 8.1的版本时部署过程中发生的错误的解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.4及更高版本

* 扩展或技术(Fastly、New Relic等) 版本PHP 8.1

## 问题

在升级到支持PHP 8.1的版本时，在部署过程中出现以下错误。

```PHP
{{E: Error parsing configuration files:

applications: Uncaught exception: The "json" extension is not supported for php:8.1
at <script>:109:12
throw("The \"" + unsupported_extensions[0] + "\" extension is not supported for " + service.type);
^
E: Error: Invalid configuration files, aborting build}}
```

## 原因

PHP 8.1已包含JSON支持，并且不需要单独安装扩展。

## 解决方案

从`.magento.app.yaml`中的&#x200B;**运行时** > **扩展**&#x200B;部分删除JSON并重新部署。

## 相关阅读

在我们的开发人员文档中[PHP应用程序](https://devdocs.magento.com/cloud/project/magento-app-php-application.html)。
