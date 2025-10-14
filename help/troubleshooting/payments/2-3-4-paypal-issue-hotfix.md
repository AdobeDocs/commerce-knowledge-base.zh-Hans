---
title: 2.3.4 PayPal问题修补程序
description: 本文修复了在PayPal Express结帐中选择区域时在下订单过程中收到的错误。 问题是由于Adobe Commerce v2.3.4版本中的更改引起的，与如何解析PayPal Express签出地址字段相关。
exl-id: 9f5ec100-49b0-4ac5-8951-32b5c4fe6bed
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 2.3.4 PayPal问题修补程序

本文修复了在PayPal Express结帐中选择区域时在下订单过程中收到的错误。 问题是由于Adobe Commerce v2.3.4版本中的更改引起的，与如何解析PayPal Express签出地址字段相关。

## 受影响的版本和产品

* 云基础架构上的Adobe Commerce v2.3.4
* Adobe Commerce内部部署v2.3.4

## 问题

在PayPal Express结帐中下订单期间输入国家和地区时出错。 对于地址部分中的区域字段是文本字段（与下拉菜单相反）的任何国家/地区，该问题都可重现。

<u>重现问题的步骤</u> ：

1. 启用PayPal Express签出。
1. 以访客身份或在登录时将产品添加到购物车。
1. 去结帐。
1. 选择您的送货地址。 例如，*UK* 。 然后在&#x200B;**省/市/自治区**&#x200B;字段中输入输入。 例如，*诺丁汉郡*。
1. 单击&#x200B;**下单**&#x200B;按钮下单。 您会收到成功的订单页面和订单确认电子邮件。

<u>预期结果：</u>

已成功下订单。

<u>实际结果：</u>

单击“订单”按钮时，系统将显示错误：

```
Error 500: NOTICE: PHP message: PHP Fatal error: Uncaught Error: Call to a member
  function getId() on null in httpdocs/vendor/magento/module-paypal/Model/Api/Nvp.php:1527
```

## 解决方案

对于Adobe Commerce本地商家：应用[修补程序，](https://magento.com/tech-resources/download#download2353)，该修补程序可从“我的帐户”中[magento.com](https://magento.com)门户的“下载”部分获得。

对于Adobe Commerce on cloud infrastructure商家：Adobe在适用于Commerce v1.0.2的云修补程序中包含此修补程序。请参阅我们的开发人员文档中的[Commerce的云修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches?itm_source=devdocs&itm_medium=quick_search&itm_campaign=federated_search&itm_term=cloud%20patche)发行说明，查找有关应用最新软件包的说明。

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 相关阅读

* [发行信息> Adobe Commerce 2.3.4发行说明>应用Adobe Commerce 2.3.4的区域修补程序的PayPal Express签出问题以解决我们开发人员文档中的关键PayPal Express签出问题](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/release-notes-2-3-4-commerce.html#apply-the-paypal-express-checkout-issue-with-region-patch-for-magento-234-to-address-a-critical-paypal-express-checkout-issue)。
