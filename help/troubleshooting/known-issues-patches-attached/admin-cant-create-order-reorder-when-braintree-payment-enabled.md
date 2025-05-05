---
title: 启用Braintree付款后，管理员无法创建订单/重新订单
description: 本文为Adobe Commerce 2.4.5问题提供了一个修补程序，在该问题中，启用Braintree支付方法后，管理员用户无法为客户创建订单或重新订单。
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# 启用Braintree付款后，管理员无法创建订单/重新订单

本文为Adobe Commerce 2.4.5问题提供了一个修补程序，在该问题中，启用Braintree支付方法后，管理员用户无法为客户创建订单或重新订单。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.5
* Adobe Commerce内部部署2.4.5
* Magento Open Source2.4.5

## 问题

<u>重现步骤</u>：

1. 已使用核心Braintree集成(**商店** > **配置** > **销售** > **付款方式** > **Braintree**)。
1. 使用Luma店面下订单。
1. 转到“管理员UI”>**Sales**。
1. 尝试为客户创建新订单，或转到之前下单的订单并单击&#x200B;**重新订购**。

<u>预期的结果</u>：

启用Braintree付款方式后，管理员用户即可为客户成功创建订单和重新订单。

<u>实际结果</u>：

启用Braintree付款方式后，管理员用户无法为客户创建订单或重新订单，并返回以下错误：

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## 原因

不正确的类依赖项(`vendor/paypal/module-braintree-core/Block/Form.php`)

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请单击以下链接：

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>此外，对于Adobe Commerce on cloud infrastructure商家：Adobe已在Commerce版本1.0.18的云修补程序中包含此修补程序。请参阅我们的开发人员文档中的[Commerce的云修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches)发行说明，查找有关应用最新软件包的说明。

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.4.5
* Adobe Commerce内部部署2.4.5
* Magento Open Source2.4.5

>[!NOTE]
>
>该修补程序与任何其他Adobe Commerce及Magento Open Source版本和版本不兼容。

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
