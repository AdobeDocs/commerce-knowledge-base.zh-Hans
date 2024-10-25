---
title: '顶点地址清理：不允许使用不同的地址'
description: 本文讨论当用户尝试输入**不同**帐单和送货地址，并启用顶点地址验证时，店面不允许用户输入该地址问题的解决方案。
exl-id: a481b044-3b74-4792-abc6-249a182c49e1
feature: B2B, Orders, Shipping/Delivery, Checkout
role: Developer
source-git-commit: a1046621259ea49eab74cd6ba3bba550e0c70283
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 顶点地址清理：不允许使用不同的地址

本文介绍当用户尝试输入&#x200B;**不同的**&#x200B;帐单和送货地址，并启用顶点地址验证时，店面不允许用户输入该地址问题的解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.5-p1

## 问题

<u>重现步骤</u>：

1. 转到“管理员”>“**商店**”>“**配置**”>“**销售**”>“**地址清理**”。
1. 从&#x200B;**使用顶点地址清理**&#x200B;下拉列表和&#x200B;**保存配置**&#x200B;中选择&#x200B;*已启用*。
1. 作为访客前往前端，然后将产品添加到购物车。
1. 单击“购物车”图标，然后&#x200B;**继续结帐**。
1. 填写地址字段。
1. 选择所需的&#x200B;**送货方法**&#x200B;并单击&#x200B;**下一步**。
1. 再次单击&#x200B;**下一步**&#x200B;按钮。
1. 取消选中&#x200B;**我的帐单和送货地址** **相同**，然后输入新的帐单地址（不同于地址）。
1. 单击&#x200B;**更新**&#x200B;按钮，然后单击&#x200B;**更新地址**。

<u>预期的结果</u>：

用户会看到不同的账单地址和送货地址。

<u>实际结果</u>：

当用户点击更新时，账单地址和运送地址恢复为相同。

## 原因

顶点地址验证失败。

## 解决方案

禁用顶点地址验证或升级到2.4.0。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知问题：在多送货结帐中删除奖励点时出现404错误](/help/troubleshooting/storefront/magento-2-4-0-404-error-removing-rewards-points-on-multi-shipping-checkout.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题 — 出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：Klarna缺少“退款”标签](/help/troubleshooting/payments/magento-2-4-0-known-issue-missing-refund-label-in-klarna.md)
* [Adobe Commerce 2.4.0已知问题：管理员的“创建新订单”页面上缺少两个按钮](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-create-new-order-buttons-missing.md)
* [Adobe Commerce 2.4.0已知问题：启用Braintree后，Venmo部分发票发行](/help/troubleshooting/payments/magento-2-4-0-2-4-1-enable-braintree-venmo-partial-invoice-issue.md)
* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
* [Adobe Commerce 2.4.0已知问题：启用了Amazon Pay，在使用返回标准结帐时缺少付款方法](/help/troubleshooting/payments/magento-2-4-0-known-issue-amazon-pay-no-payment-methods.md)
* [Adobe Commerce 2.4.0已知问题： 2.4.0安装因过时的存储缓存而失败](/help/troubleshooting/installation-and-upgrade/magento-2-4-0-known-issue-2-4-0-installation-fails-with-outdated-stores-cache.md)
