---
title: 核心Adobe Commerce支付集成已弃用
description: 由于支付服务指令PSD2(请参阅我们的用户指南中有关[支付服务指令](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html)的详细信息)和许多API的不断发展，Adobe Commerce的多项核心支付集成可能会变得过时，并且在未来不再符合安全性要求。 为此，许多核心支付集成已经或即将弃用，我们建议迁移到相应的Commerce Marketplace扩展。 请阅读以下文章的其余部分，以查看最近弃用的支付集成。 可在我们的用户指南中找到每个**Status**链接。 **以下集成将从Adobe Commerce的2.4.0版本中全部删除，已在2.3版本中弃用。**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# 核心Adobe Commerce支付集成已弃用

由于支付服务指令PSD2（请参阅我们的用户指南中有关[支付服务指令](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html)的详细信息）和许多API的不断发展，许多Adobe Commerce核心支付集成可能会过时，并且将来不再符合安全要求。 为此，许多核心支付集成已经或即将弃用，我们建议迁移到相应的Commerce Marketplace扩展。 请阅读以下文章的其余部分，以查看最近弃用的支付集成。 可在我们的用户指南中找到每个&#x200B;**状态**&#x200B;链接。 **以下集成将从Adobe Commerce的2.4.0版本中全部删除，已在2.3版本中弃用。**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>支付方式集成</strong></td>
<td style="width: 226.364px;"><strong>状态</strong></td>
<td style="width: 226.364px;"><strong>Adobe Commerce 2.X推荐</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Worldpay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">自2.3.5</a><br>2.4.0起已弃用 — 将完全删除</td>
<td style="width: 226.364px;">询问您的支付提供商他们建议采用哪种解决方案来符合PSD2的要求。</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">自2.3.4</a><br>2.4.0起已弃用 — 将完全删除</td>
<td style="width: 226.364px;">请改用Commerce Marketplace中的<a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">正式扩展</a>。</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (直接Post)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">自2.3.1</a><br>2.4.0起已弃用 — 将完全删除</td>
<td style="width: 226.364px;">请改用Commerce Marketplace中的<a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">正式扩展</a>。</td>
</tr>
<tr>
<td style="width: 225.455px;">网络资源</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">自2.3.3</a><br>2.4.0起已弃用 — 将完全删除</td>
<td style="width: 226.364px;">请改用Commerce Marketplace中的<a href="https://marketplace.magento.com/cybersource-global-payment-management.html">正式扩展</a>。</td>
</tr>
<tr>
<td style="width: 225.455px;">eWay</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">自2.3.3</a><br>2.4.0起已弃用 — 将完全删除</td>
<td style="width: 226.364px;">询问您的支付提供商他们建议采用哪种解决方案来符合PSD2的要求。</td>
</tr>
</tbody>
</table>

**请注意，PayPal核心支付方式集成将不会被弃用或删除，并且所有2.3.x和2.4.x版本仍支持该集成。**

## 如何保持贵机构在支付过程中的安全

对于仍在使用已弃用支付集成的所有Adobe Commerce和Magento Open Source部署，请按照以下建议操作，以确保客户的支付安全、不会拒绝支付，并准备升级到Adobe Commerce 2.4.0：

* 如上表所述，从[Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043)安装和配置官方付款方式扩展。
* 在Admin中禁用已弃用的付款集成（将&#x200B;**Enabled**&#x200B;配置选项设置为&#x200B;*No* ），以便它们不再作为付款选项显示在您的店面上。 请确保所有新订单都改为通过扩展集成进行支付。
* 由于来自Commerce Marketplace的新集成将无法处理通过使用已弃用的支付集成进行的支付交易，我们建议在某个并行时段同时使用这两种支付方法；但仅用于完成已过帐的交易和可能的退款。 要实现此目的，请保持禁用已弃用的支付方式，但保留所有配置字段。
