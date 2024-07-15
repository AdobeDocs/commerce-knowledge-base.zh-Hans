---
title: 'Adobe Commerce 2.4.0已知问题：订单显示错误'
description: '本文为Adobe Commerce中的已知问题提供了解决方法，以解决订单显示错误。 当登录的客户在**我的帐户**菜单(**我的帐户&amp；gt；我的订单**)中查看其订单时，当有11个订单时，订单网格无法将每页的订单数从第2页切换为20个。 此外，如果每页显示的订单数超过配置的数量，则在导航到包含订单的最后一页时，更改每页显示的订单数将会生成错误消息：*您未下达任何订单*。 此问题将在Adobe Commerce 2.4.1中得以解决。'
exl-id: a6d300e1-1cbc-42b9-997d-d72f8765517b
feature: B2B, Categories, Storefront
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知问题：订单显示错误

本文为Adobe Commerce中出现的订单显示错误已知问题提供了解决方法。 当登录的客户在&#x200B;**我的帐户**&#x200B;菜单（**我的帐户>我的订单**）中查看其订单时，当有11个订单时，订单网格无法将每页的订单数从第2页切换为20个。 此外，如果每页显示的订单数超过配置的数量，则在导航到包含订单的最后一页时，更改每页显示的订单数会生成错误消息：*您未下任何订单*。 此问题将在Adobe Commerce 2.4.1中得以解决。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>先决条件</u>

* 已安装Adobe Commerce 2.4.0。
* 创建至少一个类别和一个简单产品。

<u>重现步骤</u>

1. 使用产品创建11个订单。
1. 转到&#x200B;**我的帐户**。
1. 转到&#x200B;**我的订单**。
1. 单击第二页以在“订单”网格中显示第11个订单。
1. 从下拉菜单中选择&#x200B;**显示=每页20**。

<u>预期的结果</u>

所有11个订单都会按预期显示在第一页。

<u>实际结果</u>

显示&#x200B;*您未下订单*&#x200B;错误消息。

## 解决方法

解决方法是让采购员重新打开&#x200B;**我的订单**&#x200B;页面，然后订单列表将正确显示。 此问题将在下一个版本Adobe Commerce 2.4.1中修复，该版本计划于2020年第4季度发布。

## 我们的支持知识库中的相关读物

* [Adobe Commerce 2.4.0已知问题 — 无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Storefront上显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价](/help/troubleshooting/miscellaneous/magento-2-4-0-b2b-admin-can-t-add-configurable-product-to-quote.md)
