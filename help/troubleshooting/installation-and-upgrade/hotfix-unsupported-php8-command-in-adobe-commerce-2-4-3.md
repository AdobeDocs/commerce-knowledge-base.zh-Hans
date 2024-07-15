---
title: Adobe Commerce升级2.4.3、2.3.7-p1 PHP致命错误修补程序
description: '本文修复了商家尝试升级到Adobe Commerce（所有部署方法）或Magento Open Source2.4.3或2.3.7-p1时出现以下错误的问题：'
exl-id: 1c472214-8387-403e-b2d2-d3f3c9e1da6a
feature: Install, Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Adobe Commerce升级2.4.3、2.3.7-p1 PHP致命错误修补程序

本文修复了商家尝试升级到Adobe Commerce（所有部署方法）或Magento Open Source2.4.3或2.3.7-p1时出现以下错误的问题：

*PHP致命错误：未捕获错误：调用&lt;...>Magento\Framework\Filesystem\Directory\str_contains：74*&#x200B;中的未定义函数/magento/vendor/magento/framework/Filesystem/Directory/DenyListPathValidator.php()

此问题将在2.4.4、2.4.3-p1和2.3.7-p2版本的范围内修复。

## 受影响的版本和产品

* 升级到2.3.7-p1或2.4.3时的Adobe Commerce（所有部署方法）。
* 升级到2.3.7-p1或2.4.3时Magento Open Source。

## 问题

此问题是由使用PHP 8的新Adobe Commerce 2.4.3和2.3.7-p1版本仅函数`str_contains`导致的。 Adobe Commerce 2.4.3和2.3.7-p1仅与PHP 7.4兼容，因此无法使用此函数。

<u>重现问题的步骤</u> ：

尝试升级到Adobe Commerce 2.4.3或2.3.7-p1。

<u>预期结果：</u>

升级成功。

<u>实际结果：</u>

PHP致命错误。

## 解决方案

作为解决方法，您可以在CLI/终端中运行以下命令：从Magento根文件夹运行`composer require symfony/polyfill-php80`或安装编辑器修补程序。

为了修复2.4.3的问题，Adobe Commerce（所有部署方法）和Magento Open Source商应应用修补程序：

[AC-384_Fix_Incompatible_PHP_Method__2.4.3_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.4.3_ce.patch.zip)

为了修复2.3.7-p1的问题，Adobe Commerce（所有部署方法）和Magento Open Source商家应应用修补程序：

[AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch](assets/AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch.zip)

## 如何应用修补程序

有关说明，请参阅[如何应用Magento](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 相关阅读

GitHub [Magento2.4.3 EE #33680](https://github.com/magento/magento2/issues/33680)不支持的PHP 8命令
