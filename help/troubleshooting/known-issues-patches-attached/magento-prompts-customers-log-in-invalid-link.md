---
title: Adobe Commerce提示客户登录无效链接
description: 本文提供了一个指向已知Adobe Commerce 2.3.5问题的修补程序的链接，该问题会提示客户登录，但重新发送确认电子邮件的链接不起作用。
exl-id: 8adef44f-56a6-4f57-a9b5-fb8583d8ae8d
feature: Logs
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce提示客户登录无效链接

本文提供了一个指向已知Adobe Commerce 2.3.5问题的修补程序的链接，该问题会提示客户登录，但重新发送确认电子邮件的链接不起作用。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.3.5

## 问题

Adobe Commerce通过显示此消息来提示客户登录： *&quot;此帐户未确认。 单击此处以重新发送确认电子邮件“*”。 **单击此处**&#x200B;链接应会打开发送确认链接页面，但该页面处于非活动状态。

## 解决方案

Adobe Commerce技术资源中提供了此问题的修补程序：[重新发送帐户确认电子邮件链接问题修补程序，适用于Adobe Commerce 2.3.5](https://magento.com/tech-resources/download?_ga=2.193540264.409362045.1590506265-807369446.1578680711#download2368)。 Adobe Commerce 2.3.6将提供永久修复，该版本计划于2020年第4季度发布。

有关如何应用编辑器修补程序的说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 相关阅读

有关Adobe Commerce 2.3.5已知问题的支持知识库和开发人员文档中的文章：

* [Adobe Commerce 2.3.5已知问题：虚拟产品多发运订单](/help/troubleshooting/miscellaneous/magento-2-3-5-known-issue-virtual-product-multi-ship-orders.md)
* [Adobe Commerce 2.3.5中的产品比较已知问题](/help/troubleshooting/storefront/product-comparison-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5、2.3.5-p1修补程序：国家/地区付款问题](/help/troubleshooting/known-issues-patches-attached/magento-2-3-5-2-3-5-p1-patch-country-payment-issue.md)
* [Adobe Commerce提示客户登录无效链接](/help/troubleshooting/known-issues-patches-attached/magento-prompts-customers-log-in-invalid-link.md)
* [Adobe Commerce 2.3.5中的批量操作产品计数已知问题](/help/troubleshooting/miscellaneous/bulk-action-product-count-known-issue-in-magento-2-3-5.md)
* [Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序](/help/troubleshooting/payments/patch-for-amazon-pay-checkout-issue-in-magento-2-3-5-p1.md)
* [Adobe Commerce 2.3.5已知问题](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#known-issues)
