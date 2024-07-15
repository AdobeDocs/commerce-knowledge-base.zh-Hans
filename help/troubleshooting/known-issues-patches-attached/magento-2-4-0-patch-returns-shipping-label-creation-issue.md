---
title: 'Adobe Commerce 2.4.0修补程序：返回发货标签创建问题'
description: 当打印客户退货的送货标签时出现问题时，本文会为已知的Adobe Commerce 2.4.0问题提供一个修补程序。
exl-id: f78f8d7e-29e9-4d6c-83f6-cd5afa1d7d9c
feature: B2B, Orders, Returns, Communications, Shipping/Delivery
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Adobe Commerce 2.4.0修补程序：返回发货标签创建问题

当打印客户退货的送货标签时出现问题时，本文会为已知的Adobe Commerce 2.4.0问题提供一个修补程序。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 问题

<u>要再现的步骤：</u>

1. 使用以下核心配送方式之一下单并完成订单：FedEx、DHL、UPS和USPS。
1. 为此订单创建和授权退货。
1. 打开授权的&#x200B;**退货信息**&#x200B;页面，然后单击&#x200B;**创建送货标签**&#x200B;按钮。
1. 选择配送方式，将产品添加到包装中，然后单击“保存”。

<u>预期结果：</u>

已成功创建配送标签，您看到一条消息： *您已创建配送标签。*

<u>实际结果：</u>

**返回信息**&#x200B;页已损坏，您在“返回信息”页上看到一条错误消息： *对此分区进行了常规信息更改但尚未保存。 此选项卡包含无效数据*。

## 解决方案

应用本文中提供的[patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[MC-35984-2.4.0-CE-composer.patch](assets/MC-35984-2.4.0-CE-composer.patch.zip)

该修补程序还能够以两种格式（`.git`和`.composer`）下载，它们位于[Adobe Commerce Downloads](https://magento.com/tech-resources/download)页左侧列导航栏中&#x200B;**修补程序**&#x200B;下。 搜索MC-35984修补程序。

## 如何应用修补程序

有关说明，请参阅我们的支持知识页中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 我们的支持知识库中的相关读物：

* [Adobe Commerce 2.4.0已知问题：店面中显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Braintree支付方式未显示在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
* [Adobe Commerce 2.4.0中的配送标签创建已知问题](/help/troubleshooting/known-issues-patches-attached/shipping-labels-creation-known-issue-in-magento-2-4-0.md)
