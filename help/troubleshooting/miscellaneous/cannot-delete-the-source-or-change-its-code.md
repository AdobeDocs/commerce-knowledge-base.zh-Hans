---
title: 无法删除源或更改其代码
description: 本文修复了无法完全删除源和/或更改其代码的情况。
exl-id: dbdb4d62-9138-4a3d-a58f-8671f1dc5b42
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 无法删除源或更改其代码

本文修复了无法完全删除源和/或更改其代码的情况。

## 问题

无论是否分配产品，均无法删除源。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本），已安装Magento清单
* Adobe Commerce内部部署2.3.0及更高版本，安装了Magento清单
* 安装了Magento清单的Magento Open Source2.3.0及更高版本

## 原因

根据设计，不可能完全删除源和/或更改其代码。

完全删除来源会导致订单数据出现问题，因为来源是产品库存、订单、发运数据等的一部分。

代码对于将源连接到订单至关重要。 这是源的唯一ID，禁止编辑。

## 解决方案

您可以通过转移库存或从某个地点的所有发运中删除产品来从产品中删除来源。

如果需要从[SSA](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/inventory/basics/selection-reservations)计算和Adobe Commerce库存订单处理中删除来源，则可以禁用该来源。 禁用的来源会保留所有数据、分配的产品和库存数量，并可随时重新启用以重新开始发运。

有关如何禁用源的详细信息，请参阅[创建源指南](https://github.com/magento/inventory/wiki/Create-Sources#disable-sources)。
