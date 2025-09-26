---
title: Adobe Commerce 2.4.0已知问题 — 出口税率不起作用
description: 本文为Adobe Commerce 2.4.0的已知问题提供了一个解决方案，该问题导致**导出税率**按钮不起作用。
exl-id: 29a34a1f-d23a-43cb-ac1f-8711ce25fa6c
feature: Data Import/Export, Orders
role: Developer
source-git-commit: 9cd9720a73b8ecde3baf6a7a5b5732ad1330feee
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知问题 — 出口税率不起作用

本文为Adobe Commerce 2.4.0的已知问题提供了一个解决方案，该问题导致“**导出税率**”按钮不起作用。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.0
* Adobe Commerce内部部署2.4.0

## 问题

<u>要再现的步骤：</u>

1. 转到Commerce管理面板> **商店** > **税则**。
1. 单击&#x200B;**添加新税则**&#x200B;按钮。
1. 单击&#x200B;**导出税率**&#x200B;按钮的文本。

   ![magento_export_tax_rates.png](assets/mceclip0.png)

<u>预期的结果</u>：

下载包含税率的`tax_rates.csv`文件。

<u>实际结果</u>：

未下载.csv文件。

## 解决方案

解决方法：

单击&#x200B;**导出税率**&#x200B;按钮的左下边缘以导出`tax_rates.csv`文件。

![magento_export_tax_rates.png](assets/mceclip1.png)

计划在2.4.1补丁中解决此问题。

## 相关阅读

在我们的支持知识库中：

* [Adobe Commerce 2.4.0已知问题： Braintree付款方法未出现在多地址结帐中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)。
* [Adobe Commerce 2.4.0已知问题 — 客户活动上的刷新不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)。
* [Adobe Commerce 2.4.0已知问题：“将选定内容添加到购物车”按钮不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-add-selections-to-my-cart-does-not-work.md)。
