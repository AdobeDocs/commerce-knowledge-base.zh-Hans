---
title: 使用Authorize.net付款方式时结账卡住
description: 本文针对Adobe Commerce 2.3.X问题提供了说明和修复，如果使用Authorize.net，并且浏览器控制台日志中显示*“无法读取值为null的属性‘长度’”错误消息，则签出会卡住。
exl-id: 01dc1147-4010-4dc5-81f3-3b3015a8c47c
feature: Cache, Checkout, Console, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 使用Authorize.net付款方式时结账卡住

本文针对Adobe Commerce 2.3.X问题提供了说明和修复，如果使用Authorize.net，则签出卡住，并在浏览器控制台日志中显示&#x200B;*“无法读取null的属性‘长度’*&#x200B;错误消息。

## 受影响的产品和版本

* Adobe Commerce 2.3.X

>[!NOTE]
>
>核心Adobe Commerce Authorize.Net支付集成自2.3.4之后已被弃用，在2.4.0中已完全删除。请改用[Adobe Commerce [!DNL Marketplace]](https://commercemarketplace.adobe.com/)中适合您需求的扩展。

## 问题

<u>重现步骤</u>

1. 在Commerce管理员中配置Authorize.net支付方式。
1. 去店面。
1. 将产品添加到购物车并继续结帐。
1. 选择Authorize.net作为付款方式。
1. 单击&#x200B;**下单**。

<u>预期的结果</u>

Authorize.net iframe已加载。

<u>实际结果</u>

此时将显示Ajax旋转图标，并且页面从不加载。 浏览器控制台日志中显示以下JS错误： *&#39;Uncaught TypeError：无法读取b处为null的属性&#39;length&#39; (jstest.authorize.net/v1/AcceptCore.js:1)&#39;*)

## 原因

此问题最常见的原因之一是，在Commerce管理员的Authorize.Net配置中未指定公共客户端密钥。

## 解决方案

在&#x200B;**存储** > **设置** > **配置** > **销售** > **付款方法**&#x200B;下，在&#x200B;**Authorize.net**&#x200B;部分中，检查是否在&#x200B;**公共客户端密钥**&#x200B;字段中指定了值。 如果为空，请输入您的Authorize.Net商家帐户中的键值。

对于要应用的更改，请通过运行

```bash
bin/magento cache:clean
```
