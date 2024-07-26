---
title: 在沙盒环境中信用卡付款失败
description: 本文介绍了为什么在具有PayPal API的Sandbox环境中测试信用卡失败。
exl-id: 65fd08e0-eefc-47f3-8964-bef3610e6182
feature: Orders, Payments
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 在沙盒环境中信用卡付款失败

本文介绍了为什么在具有PayPal API的Sandbox环境中测试信用卡失败。

## 受影响的产品和版本


* Adobe Commerce 2.4.0 - 2.4.4 ，所有部署选项，带[付款服务](https://marketplace.magento.com/magento-payment-services.html)

## 问题

使用来自PayPal的测试Visa信用卡`4111 1111 1111 1111`时，有时由于PayPal欺诈政策而导致失败，并出现以下错误：

```bash
Error happened when processing the request. Please try again later.
```

## 原因

当PayPal标记特定测试信用卡号以进行欺诈时，将显示此错误。 发生这种情况是因为它是全球每个使用PayPal API进行测试的人员使用的测试信用卡号码。

## 解决方案

使用其他测试信用卡。 要生成可用于测试的模拟信用卡，请执行以下操作：

1. 转到PayPal开发人员门户[信用卡生成器](https://developer.paypal.com/developer/creditCardGenerator/)页面。
1. 登录到PayPal开发人员门户仪表板。
1. 生成测试信用卡。
