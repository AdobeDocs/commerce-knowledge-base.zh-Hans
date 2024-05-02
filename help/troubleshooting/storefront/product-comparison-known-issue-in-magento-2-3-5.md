---
title: Adobe Commerce 2.3.5中的产品比较已知问题
description: 本文提供了有关如何避免在Adobe Commerce内部部署2.3.5和Adobe Commerce on cloud infrastructure 2.3.5中出现的已知[产品比较](https://docs.magento.com/user-guide/marketing/product-compare.html)问题的建议。
exl-id: 1488e2db-4a5d-4963-b48e-b84f760582d1
feature: Products, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Adobe Commerce 2.3.5中的产品比较已知问题

本文就如何避免已知问题提供了建议 [产品比较](https://docs.magento.com/user-guide/marketing/product-compare.html) Adobe Commerce内部部署2.3.5和Adobe Commerce中的cloud infrastructure 2.3.5问题。

## 受影响的产品和版本

* Adobe Commerce内部部署2.3.5
* 云基础架构上的Adobe Commerce 2.3.5

## 问题

当用户尝试比较不同商店视图中的产品并且一个产品的可比属性为空值时，Adobe Commerce显示损坏的比较产品页面。

## 解决方案

为可比较的产品属性指定非空值，或者为属性使用默认商店视图值。 可比较的属性值不能为空。

>[!NOTE]
>
>产品属性设置为使用进行比较 **Storefront上的比较** 配置设置。 欲了解更多信息，请参见 [创建产品属性](https://docs.magento.com/user-guide/stores/attribute-product-create.html#step-4-describe-the-storefront-properties) 在我们的用户指南中。

Adobe Commerce 2.3.6中将会提供相应的修复，该版本计划于2020年第4季度发布。

您可以在GitHub中查看此修补程序（请考虑，此修补程序未通过回归测试，不是正式的修补程序）： <https://github.com/magento/magento2/pull/27662>

## 相关阅读

<ul><li>适用于Adobe Commerce 2.3.5已知问题的Adobe Commerce支持知识库文章：<ul>
<li>
<p title="在Adobe Commerce 2.3.5中无法正确处理包含虚拟产品的多配送订单"><a href="/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md">在Adobe Commerce 2.3.5中无法正确处理包含虚拟产品的多配送订单</a></p>
</li>
<li><a href="/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md">Adobe Commerce 2.3.5中的批量操作产品计数已知问题</a></li>
<li>
<p title="Adobe Commerce中的云基础设施国家/地区支付方法问题，以及Adobe Commerce内部部署2.3.5和2.3.5-p1"><a href="/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md">Adobe Commerce中的云基础设施国家/地区支付方法问题，以及Adobe Commerce内部部署2.3.5和2.3.5-p1</a></p>
</li>
<li>
<p title="Adobe Commerce会提示客户登录，但会提供无效链接"><a href="/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md">Adobe Commerce会提示客户登录，但会提供无效链接</a></p>
</li>
<li>
<p title="Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序"><a href="/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md">Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序</a></p>
</li>
</ul>
</li><li><a href="https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues">Adobe Commerce 2.3.5已知问题</a> 在我们的开发人员文档中</li></ul>
