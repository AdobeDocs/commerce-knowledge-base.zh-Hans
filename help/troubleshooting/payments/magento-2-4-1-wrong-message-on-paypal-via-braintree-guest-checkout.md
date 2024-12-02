---
title: Adobe Commerce 2.4.1：PayPalBraintree访客结帐时出现错误消息
description: 本文介绍了一个已知的Adobe Commerce 2.4.1问题：如果禁用访客签出，则尝试通过Braintree使用PayPal下达订单的访客客户将收到一则非信息性错误消息。
exl-id: 758f5c57-997e-4aca-b299-9934c94fa121
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Adobe Commerce 2.4.1：PayPalBraintree访客结帐时出现错误消息

本文介绍了一个已知的Adobe Commerce 2.4.1问题：如果禁用访客签出，则尝试通过Braintree使用PayPal下达订单的访客客户将收到一则非信息性错误消息。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0、2.4.1
* 云基础架构上的Adobe Commerce 2.4.0、2.4.1

## 问题

当从后端禁用访客结帐，并从迷你购物车或购物车中选择PayPal通过Braintree付款选项时，会显示非特定错误。

<u>先决条件</u>：

1. 在Commerce管理员中，在&#x200B;**商店** > **配置** > **销售** > **签出**&#x200B;下，设置&#x200B;**允许来宾签出** = *否*。
1. 按照用户指南中的[Braintree](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/braintree?)所述，通过Braintree启用PayPal。

<u>重现步骤</u>：

1. 将产品作为访客添加到购物车。
1. 选择&#x200B;**迷你购物车**&#x200B;并单击&#x200B;**使用PayPal支付**。
1. 完成Paypal结帐，然后您将登录到“订单审核”页面。
1. 选择&#x200B;**配送方式**。
1. 单击&#x200B;**下单**。

<u>预期的结果</u>：

当客户单击迷你购物车或购物车页面上的PayPal按钮时，应向客户显示以下消息：

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

如果您启用直接Paypal而不使用Braintree，则此方案的行为方式不同。 它不允许来宾用户继续支付流程。 当访客用户单击迷你购物车中的PayPal按钮时，它将显示以下消息：

<pre><code class="language-bash">To check out, please sign in with your email address.</code></pre>

<u>实际结果</u>：

客户将被重定向到“购物车”页面，并显示以下消息：

<pre><code class="language-bash">The customer email is missing. Enter and try again.</code></pre>

## 解决方法

此问题的解决方法是客户可以在禁用来宾签出的商店（登录用户不使用来宾签出）登录。 已在Adobe Commerce版本2.4.2中修复此问题。

## 相关阅读

* 在我们支持知识库中，[Adobe Commerce购物车中产品数量的最佳实践](https://support.magento.com/hc/en-us/articles/360048550332)。
* [订单处理教程：步骤1。 在开发人员文档中将项目添加到购物车](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/order-add-items/)
* [GraphQL签出教程：步骤1。 在开发人员文档中将产品添加到购物车](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/add-product-to-cart/)
