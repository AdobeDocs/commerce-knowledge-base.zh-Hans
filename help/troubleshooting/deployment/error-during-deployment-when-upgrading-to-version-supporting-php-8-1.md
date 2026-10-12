---
title: 升级到支持PHP 8.1的版本时，在部署过程中出错
description: 本文提供了在升级到支持PHP 8.1的版本时部署过程中发生的错误的解决方案。
exl-id: bdc4a355-4f2b-49a7-9c5d-63c950f7ca30
feature: Deploy, Observability
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%
---
# 升级到支持PHP 8.1的版本时，在部署过程中出错

本文提供了在升级到支持PHP 8.1的版本时部署过程中发生的错误的解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.4。 及更高版本

* 扩展或技术（Fastly、New Relic等） 版本PHP 8.1

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

在我们的开发人员文档中[PHP应用程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/php-settings)。
