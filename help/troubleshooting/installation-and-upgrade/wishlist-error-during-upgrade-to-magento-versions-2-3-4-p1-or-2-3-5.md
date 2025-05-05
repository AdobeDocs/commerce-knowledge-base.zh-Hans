---
title: 升级到Adobe Commerce版本2.3.4-p1或2.3.5期间出现愿望清单错误
description: 本文修复了在升级到Adobe Commerce版本2.3.4-p1和2.3.5时，与升级到这些版本期间出现愿望清单错误相关的已知问题。
exl-id: 97479615-bf3f-4544-a9c1-8f19ba74318e
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 升级到Adobe Commerce版本2.3.4-p1或2.3.5期间出现愿望清单错误

本文修复了在升级到Adobe Commerce版本2.3.4-p1和2.3.5时，与升级到这些版本期间出现愿望清单错误相关的已知问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.4-p1和2.3.5
* Adobe Commerce内部部署2.3.4-p1和2.3.5

## 问题

将Adobe Commerce（所有部署方法）和Magento Open Source升级到版本2.3.5或2.3.4-p1时，您可能会从模块中收到愿望清单错误（详见下文）：

```php
Magento_Wishlist
```

从Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.4-p1 **升级到版本2.3.4-p2**&#x200B;或从Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.5 **升级到版本2.3.5-p1**&#x200B;将修复该错误。

<u>重现步骤</u>：

将您的Adobe Commerce（所有部署方法）/Magento Open Source升级到版本2.3.4-p1或2.3.5。

<u>预期的结果</u>：

升级到Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.4-p1或2.3.5的升级过程会正常完成。

<u>实际结果</u>：

在升级过程中，您会收到以下错误：

```php
Module ‘Magento_Wishlist’:

Unable to apply data patch Magento\Wishlist\Setup\Patch\Data\CleanUpData for module Magento_Wishlist. Original exception message: Unable to unserialize value. Error: Syntax error
```

## 解决方案

* 如果您要升级到Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.5，请&#x200B;**升级到版本2.3.5-p1**。 Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.5-p1取代2.3.5。
* 如果您要升级到Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.4-p1，请&#x200B;**升级到版本2.3.4-p2**。 Adobe Commerce（所有部署方法）/Magento Open Source版本2.3.4-p2取代了版本2.3.4-p1。

## 相关阅读

在我们的开发人员文档中：

* 云基础架构上的[Adobe Commerce指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/overview)
* 云基础架构上的[Adobe Commerce — 升级Adobe Commerce版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)
* [Adobe Commerce内部部署和Magento Open Source — 升级Adobe Commerce应用程序和模块](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/overview)
* [愿望清单项目配置页](https://developer.adobe.com/commerce/frontend-core/guide/layouts/product-layouts/#wishlist-item-configure-page)
* [提供高级报告的模块](https://developer.adobe.com/commerce/php/development/advanced-reporting/modules/)
