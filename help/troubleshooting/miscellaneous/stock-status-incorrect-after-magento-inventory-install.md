---
title: 安装Inventory management后，库存状态不正确
description: 本文修复了在安装/升级Inventory management后库存状态不正确的问题。
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# 安装Inventory management后，库存状态不正确

本文修复了在安装/升级Inventory management后库存状态不正确的问题。

## 某些网站上的库存状态不正确

在多网站Adobe Commerce环境中首次安装或升级以拥有Inventory management后，并非所有网站都具有正确的产品库存状态。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本，已安装Inventory management
* 已安装Inventory management的Adobe Commerce内部部署2.3.0及更高版本
* 安装了Inventory management的Magento Open Source2.3.0及更高版本

## 原因

首次安装/升级时，会将所有产品分配给默认来源，并将所有数量与该来源相关联。 默认Source将分配给默认库存，并与默认网站关联。

## 解决方案

如果您有多个网站，则需要将这些网站作为Sales Channel添加到默认股票或其他自定义股票。

有关如何操作的详细信息，请参阅我们用户指南中Wiki/用户指南[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage)的Stock部分。
