---
title: 安装Inventory management后，库存状态不正确
description: 本文修复了在安装/升级Inventory management后库存状态不正确的问题。
exl-id: ae32fbe3-deab-4f31-b427-95f8b54a476f
feature: Install, Inventory, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
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

首次安装/升级时，会将所有产品分配给默认来源，并将所有数量与该来源相关联。 “默认来源”将分配给默认库存，并关联默认网站。

## 解决方案

如果您有多个网站，则需要将这些网站作为Sales Channel添加到默认股票或其他自定义股票。

请参阅 [Wiki/用户指南的Stock部分](https://docs.magento.com/m2/ce/user_guide/catalog/inventory-stock.html) ，以获取有关如何执行此操作的详细信息。
