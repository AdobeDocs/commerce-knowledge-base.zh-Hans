---
title: 'Adobe Commerce 2.4.0已知问题：创建新订单按钮缺失'
description: 本文针对订单创建页面中缺少的两个按钮，提供了Commerce管理员中已知问题的解决方法。 为新客户或现有客户创建新订单时，无法从目录中将产品添加到订单，因为缺少**按SKU添加产品**和**添加产品**按钮。 这是由于启用了JS捆绑导致的。 Adobe Commerce 2.4.1中将会提供相应的修复。
exl-id: 24ae880e-6d74-4444-9165-2744b12af81a
feature: B2B
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知问题：创建新订单按钮缺失

本文针对订单创建页面中缺少的两个按钮，提供了Commerce管理员中已知问题的解决方法。 为新客户或现有客户创建新订单时，无法从目录将产品添加到订单，因为 **按SKU添加产品** 和 **添加产品** 按钮缺失。 这是由于启用了JS捆绑导致的。 Adobe Commerce 2.4.1中将会提供相应的修复。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>重现问题的步骤</u>

1. 转到 **客户>所有客户**.
1. 单击 **编辑** 客户上的链接。
1. 单击 **创建订单** 按钮。

<u>预期结果</u>

此 **按SKU添加产品** 和 **添加产品** 按钮显示在 **创建新订单** 页面。

<u>实际结果</u>

此 **按SKU添加产品** 和 **添加产品** 上缺少按钮 **创建新订单** 页面。

## 解决方法

此问题的解决方法是为Adobe Commerce实例禁用JS捆绑包。 Adobe Commerce 2.4.1预计将于2020年第4季度发布，可修复此问题。

## 我们的支持知识库中的相关读物

* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知问题：在多送货结帐中删除奖励点时出现404错误](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0中的配送标签创建已知问题](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
