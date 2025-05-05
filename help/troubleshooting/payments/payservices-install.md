---
title: 付款服务安装疑难解答
description: 本文解释了您在安装Payment Services时可能遇到的错误，并提供了修复这些错误以便您能够完成安装的解决方案。
exl-id: 0aef7482-8834-400e-85b9-d3d3eb0ab76e
feature: Install, Orders, Payments, Saas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# 付款服务安装疑难解答

本文解释了您在安装Payment Services时可能遇到的错误，并提供了修复这些错误以便您能够完成安装的解决方案。

## 受影响的产品和版本

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html)现在与Adobe Commerce版本2.4.0到2.4.4兼容。

## 问题 — 不正确的编辑器键

安装Payment Services扩展时，您可能会看到一条错误消息，说明您在安装期间使用了不正确的编辑器密钥。

<u>重现步骤</u>：

1. 尝试[安装付款服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html)。
1. 请参阅以下错误：

   *找不到程序包magento/payment-services的匹配版本。 检查包的拼写、版本约束以及包的稳定性是否与最小稳定性（稳定）匹配。*

<u>预期的结果</u>：

您可以按照开发人员文档中的这些[安装说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html)成功安装付款服务。

<u>实际结果</u>：

在安装过程中，您会看到一条错误消息，说明您在安装过程中未使用正确的编辑器密钥。

### 原因

您在安装期间使用的编辑器密钥不正确。

### 解决方案

验证[您的编辑器密钥已链接到在付款服务注册期间使用的MagentoID](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#incorrect-composer-keys)。

## 问题 — 在多个实例中使用相同的数据空间

在每个环境中运行带有Payment Services的多环境设置。

### 解决方案

可以跨实例使用相同的API密钥，但每个实例需要使用自己的SaaS数据空间。

在创建SaaS项目时，Commerce会根据您的Commerce许可证生成一个或多个SaaS数据空间：

* Adobe Commerce — 一个生产数据空间；两个测试数据空间
* Magento Open Source — 一个生产数据空间；无测试数据空间

按照[Commerce API密钥和私钥](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#obtain-api-credentials)中的说明成功配置您的支付服务扩展。

## 问题 — PHP内存不足

在安装Payment Services扩展时，您可能会看到一条错误消息，说明您没有足够的内存来安装PHP。

<u>重现步骤</u>：

1. 尝试[安装付款服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html)。
1. 请参阅以下错误或类似错误：

   *致命错误：在phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php第52*&#x200B;行上允许的内存大小已用尽2146435072字节（尝试分配4096字节）

<u>预期的结果</u>：

您可以按照开发人员文档中的这些[安装说明](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html)成功安装付款服务。

<u>实际结果</u>：

在安装过程中，您会看到一条错误消息，说明您没有足够的内存来安装PHP。

### 原因

环境上的PHP限制未设置为足够高的阈值。

### 解决方案

在`php.ini`中增加环境上PHP[&#128279;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/install.html#not-enough-memory-for-php)的内存限制。
