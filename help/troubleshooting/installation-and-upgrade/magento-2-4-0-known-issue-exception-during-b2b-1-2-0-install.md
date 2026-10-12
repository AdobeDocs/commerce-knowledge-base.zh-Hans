---
title: Adobe Commerce 2.4.0：安装B2B 1.2.0时出现异常
description: 本文修复了在安装B2B 1.2.0时“setup：upgrade”期间引发的异常的Adobe Commerce已知问题。
exl-id: 2c1dadd9-7754-4b4c-8d37-b75c13beae5c
feature: B2B, Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%
---
# Adobe Commerce 2.4.0：安装B2B 1.2.0时出现异常

本文修复了在安装B2B 1.2.0时`setup:upgrade`期间引发的异常所导致的Adobe Commerce已知问题。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0
* B2B 1.2.0

## 问题

<u>重现步骤</u>

1. 安装Adobe Commerce并创建多个存储。
1. 创建其他存储。
1. 安装B2B 1.2.0。

>[!WARNING]
>
>任何存储区超过1个的B2B实例从1.2.0以下的版本升级或Commerce实例2.4.0以下的版本升级也会受到影响。

<u>预期的结果</u>

B2B 1.2.0安装。

<u>实际结果</u>

当`setup:upgrade`运行以安装B2B 1.2.0时，`PurchaseOrder`模块上出现此错误：

```php
Module 'Magento_PurchaseOrder':
  Unable to apply data patch Magento\PurchaseOrder\Setup\Patch\Data\InitPurchaseOrderSalesSequence
  for module Magento_PurchaseOrder. Original exception message: DDL statements
  are not allowed in transactions
```

## 解决方案

应用本文中提供的修补程序。

## Patch

该修补程序已附加到此文章，可以采用`.composer`和`.git`两种格式（解压缩文件后）下载。

要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接之一：

* [编辑器修补程序B2B-716\_composer.patch](assets/B2B-716_composer.patch.zip)
* [Git修补程序B2B-716\_git.patch](assets/B2B-716_git.patch.zip)

## 如何应用修补程序

<u>Composer修补程序</u>

有关编辑器修补程序的说明，请参阅[如何应用Adobe](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento)提供的编辑器修补程序。

<u>Git修补程序</u>

* 有关云基础架构上Adobe Commerce的Git修补程序说明，请参阅开发人员文档中的[应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。
* 有关Adobe Commerce的Git修补程序说明，请参阅开发人员文档中的[应用修补程序：自定义修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview#custom-patches)。

## 相关阅读

* [Adobe Commerce 2.4.0已知问题：Braintree支付方法未出现在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
