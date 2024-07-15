---
title: 'Adobe Commerce 2.4.0已知问题：Amazon支付，无支付方式'
description: 本文为Adobe Commerce 2.4.0的已知问题提供了一个解决方案，该问题导致客户在启用Amazon支付后使用**返回标准结帐**时缺少支付方法。
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知问题：Amazon支付，无支付方式

本文为Adobe Commerce 2.4.0的已知问题提供了一个解决方案，该问题导致客户在启用Amazon支付后使用&#x200B;**返回标准结帐**&#x200B;时缺少支付方法。

## 受影响的产品和版本

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure v2.3.5.p1和v2.4.0

<u>要再现的步骤：</u>

1. 导航到店面。
1. 将任何项目添加到购物车并继续结帐。
1. 登录到您的Amazon Pay帐户。
1. 选择地址并继续结帐。
1. 单击&#x200B;**返回标准签出**。
1. 继续结帐。

<u>预期结果：</u>

重新启动结帐后应显示付款方式。

<u>实际结果：</u>

缺少支付方式。

## 解决方案

计划针对2.4.1推出解决方案。

## 我们的支持知识库中的相关读物：

* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知问题：在多送货结帐中删除奖励点时出现404错误](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0中的配送标签创建已知问题](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题 — 出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
