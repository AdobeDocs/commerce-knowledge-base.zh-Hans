---
title: 'Adobe Commerce 2.3.7-p1已知问题：PayPal的订单总数已过时'
description: “本文为Adobe Commerce 2.3.7-p1中的已知问题提供了一个修补程序：当客户多次使用PayPal结帐功能时，他们会在购物车中获取之前订购的产品，而不是他们尝试订购的新产品。”
exl-id: ceb8f7ad-0cf7-4d42-aded-25d1dd947f5b
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Adobe Commerce 2.3.7-p1已知问题：PayPal的已过期订单总计

本文为Adobe Commerce 2.3.7-p1中的已知问题提供了一个修补程序：当客户多次使用PayPal结帐功能时，他们会在购物车中获取之前订购的产品，而不是尝试订购的新产品。
您可以从本文下载修补程序，也可以通过Quality Patches Tool (QPT)获得该修补程序。

## 受影响的版本

* Adobe Commerce（所有部署选项） 2.3.7-p1
* Magento Open Source2.3.7-p1

## 问题

使用PayPal Express Checkout付款方式下订单时，先前订购的已购产品将添加到订单中，而不是实际订单中。

<u>要再现的步骤：</u>

1. 在商店前面，将产品添加到购物车（产品A，价格50美元）。
1. 单击购物车链接以打开购物车。
1. 单击&#x200B;**PayPal结帐**&#x200B;按钮。
1. 使用您的PayPal凭据登录PayPal并提交付款。
1. 完成商店侧的订单下达。
1. 返回目录并向购物车添加其他产品（产品B，价格100美元）。
1. 单击购物车链接以打开购物车。
1. 单击&#x200B;**PayPal结帐**&#x200B;按钮。

<u>实际结果：</u>

购物车中的产品价格为$50，而不是$100。<br/>
在商店方面，订单包含产品A而不是产品B。

<u>预期结果：</u>

产品B添加到订单中。

## 解决方案

应用本文中提供的修补程序。

## Patch

使用以下链接下载包含修补程序的.zip文件： [MC42674-composer.patch.zip](assets/MC42674-composer.patch.zip)。

### 兼容的Adobe Commerce版本

* Adobe Commerce（所有部署选项） 2.3.7-p1

## 如何应用修补程序

1. 解压缩下载的.zip文件。
1. 有关进一步说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
