---
title: Adobe Commerce 2.4.0已知问题：Amazon支付，无支付方式
description: 本文为Adobe Commerce 2.4.0的已知问题提供了一个解决方案，该问题导致客户在启用Amazon支付后使用**返回标准结帐**时缺少支付方法。
exl-id: efd792c7-8970-4366-b9d1-4bf284ea96db
feature: B2B, Orders, Payments
role: Developer
source-git-commit: 05297c82b292b8ccc88018c58e991bd3a32d6ffa
workflow-type: tm+mt
source-wordcount: '218'
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
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方法未出现在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
