---
title: PWA Studio：运行开发人员模式时出现验证错误
description: 本主题讨论了一种解决方案，用于解决在Progressive Web App (PWA) Studio for Adobe Commerce中运行开发人员模式时，由于之前未创建venia-concept （Venia是PWA店面）环境文件而导致出现验证错误的情况。 此文件将包含本地开发环境的变量。
exl-id: 97d042ef-88e6-4eda-a834-2cff4de276e2
feature: Configuration
role: Developer
source-git-commit: 9d32a5971341ed8dc46e0932c10eaac4d17ec299
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# PWA Studio：运行开发人员模式时出现验证错误

本主题讨论了一种解决方案，用于解决在Progressive Web App (PWA) Studio for Adobe Commerce中运行开发人员模式时，由于之前未创建venia-concept （Venia是PWA店面）环境文件而导致出现验证错误的情况。 此文件将包含本地开发环境的变量。

## 受影响的产品和版本

* 适用于Adobe Commerce的PWA Studio

## 问题

<u>要再现的步骤</u>：

* 在适用于Adobe Commerce的PWA Studio中运行开发人员模式。

<u>预期的结果</u>：

* PWA Studio服务器正常启动。

<u>实际结果</u>：

* 您会看到验证错误，这些错误可能类似于：

```
    ⓧ  Missing required environment variables:         MAGENTO_BACKEND_URL: Connect to an instance of Adobe Commerce 2.3 by specifying its public domain name. (eg.         "https://master-7rqtwti-mfwmkrjfqvbjk.us-4.magentosite.cloud/")      ⚠  No .env file in ./packages/venia-concept. Autogenerate a .env file by running the command 'buildpack         create-env-file ./packages/venia-concept'.
```

## 原因

本地开发环境的环境变量文件缺失。 以下命令生成的文件将保存本地开发环境的变量。

## 解决方案

确保运行命令

```
npx @magento/pwa-buildpack create-env-file packages/venia-concept
```

以生成用于保存本地开发环境的变量的文件。

## 相关阅读

* Adobe Commerce的[PWA Studio文档](https://developer.adobe.com/commerce/pwa-studio/)
* [Venia Storefront（概念）](https://developer.adobe.com/commerce/pwa-studio/guides/packages/venia/)
