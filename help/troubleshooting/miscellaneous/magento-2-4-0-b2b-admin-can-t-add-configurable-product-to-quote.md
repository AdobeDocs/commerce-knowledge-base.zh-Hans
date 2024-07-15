---
title: Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价
description: 本文介绍了在管理B2B报价时Commerce Admin中的一个已知问题：无法通过**SKU**向报价中添加可配置产品。 单击**添加到报价**按钮时，**报价**编辑页面停滞加载，您无法配置产品并保存更改。 当通过**SKU**将产品添加到订单，或通过**SKU**在**高级签出** (**Admin** &amp；gt； **Customers** &amp；gt； **All Customers** &amp；gt； **Customer Edit** &amp；gt； **Manage Shopping Cart**)中添加产品时，管理员中也会出现此问题。 此问题将在Adobe Commerce 2.4.1的修补程序中得以解决。
exl-id: 73f7231b-b496-4250-b9e2-29427c772d56
feature: Admin Workspace, B2B, Catalog Management, Configuration, Products, Quotes
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Adobe Commerce 2.4.0 B2B管理员无法将可配置产品添加到报价

本文介绍了在管理B2B报价时Commerce Admin中的一个已知问题，即无法通过&#x200B;**SKU**&#x200B;向报价中添加可配置产品。 单击“**添加到报价**”按钮时，**报价**&#x200B;编辑页面加载停滞，您无法配置产品并保存更改。 当管理员将产品由&#x200B;**SKU**&#x200B;添加到订单，或在&#x200B;**高级结帐**&#x200B;中由&#x200B;**SKU**&#x200B;添加产品时，也会出现此问题（**管理员** > **客户** > **所有客户** > **客户编辑** > **管理购物车**）。 此问题将在Adobe Commerce 2.4.1的修补程序中得以解决。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>前提条件</u>

* 已安装Adobe Commerce 2.4.0。
* 已安装B2B。
* 将B2B功能设置为&#x200B;**启用公司=** *是*、**启用共享目录=** *否*&#x200B;和&#x200B;**启用B2B报价=** *是*。
* 创建客户帐户。
* 创建一个公司帐户，并将之前创建的客户作为公司管理员。
* 创建未分配给&#x200B;**Default (General)**&#x200B;的简单产品（示例： name &amp; **SKU** = TEST SIMPLE 1）。
* 让公司管理员使用上面创建的简单产品请求报价（示例：TEST SIMPLE 1）。

<u>重现步骤</u>

1. 转到Commerce管理面板。
1. 转到&#x200B;**销售>报价**。
1. 打开&#x200B;**报价**。
1. 单击&#x200B;**按SKU添加产品**&#x200B;按钮。
1. 在&#x200B;**输入SKU**&#x200B;输入字段中输入另一个（例如：TEST SIMPLE 2）产品的&#x200B;**SKU**。
1. 在&#x200B;**数量**&#x200B;输入字段中输入一些有效数量。
1. 单击&#x200B;**添加到报价**&#x200B;按钮。

<u>预期的结果</u>

* 未添加到报价单&#x200B;**网格的**&#x200B;产品（包含已创建产品的名称和&#x200B;**SKU**）按预期显示。
* 配置产品后，管理员可以按预期通过单击&#x200B;**将产品添加到报价**&#x200B;按钮，将其添加到&#x200B;**报价**。

<u>实际结果</u>

* 未添加到报价单&#x200B;**网格的**&#x200B;产品（包含所创建产品的名称和&#x200B;**SKU**）未显示。
* **Quote**&#x200B;页面加载停滞。

## 推荐

目前，编辑B2B报价时没有解决此问题的办法，但是对于订单和购物车管理，可以从&#x200B;**产品列表**&#x200B;中选择产品，而不是通过&#x200B;**SKU**&#x200B;添加产品。 Adobe Commerce 2.4.1将提供用于解决此问题的修补程序，该版本计划于2020年第4季度发布。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：无法刷新客户活动](/help/troubleshooting/miscellaneous/magento-2-4-0-refresh-on-customer-activities-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：Storefront上显示原始消息数据](/help/troubleshooting/storefront/magento-2-4-0-issue-storefront-raw-message-data-display.md)
* [Adobe Commerce 2.4.0已知问题：出口税率不起作用](/help/troubleshooting/miscellaneous/magento-2-4-0-known-issue-export-tax-rates-does-not-work.md)
* [Adobe Commerce 2.4.0已知问题：订单显示错误](/help/troubleshooting/storefront/magento-2-4-0-known-issue-orders-display-error.md)
