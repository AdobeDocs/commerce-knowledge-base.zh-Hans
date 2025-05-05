---
title: 基本价格更改对共享目录价格的影响
description: '本文回答的问题是：如果共享目录中的产品具有自定义价格，并且产品的基本价格发生了变化（例如，在计划更新之后），那么共享目录中将应用哪个价格？'
exl-id: 916678c1-ada6-4f23-af16-b107cb83ff16
feature: Catalog Management
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# 基本价格更改对共享目录价格的影响

本文回答了以下问题：如果共享目录中的产品具有自定义价格，并且产品的基本价格发生变化（例如，在计划更新后），那么共享目录中将应用哪个价格？

## 如果将自定义价格设置为百分比，则共享目录价格也会发生更改

如果将共享目录中的产品的自定义价格设置为百分比，则在更改基本价格后，产品的共享目录价格将会隐式更新。

换言之，当基本价格更新（通过正常或计划更新）时，共享目录价格在应用百分比折扣后也会更改。

## 自定义价格设置为固定时，共享目录价格不会更改

如果将共享目录中产品的自定义价格设置为“固定”，则无论我们更新基本价格的方式(通过计划更新、Adobe Commerce管理、API或导入)，共享目录中的价格都不会更改。

## 店面始终显示最低的可用价格

如果产品的基本价格发生变化并且低于相应的共享目录价格，店面会将基本价格显示为系统中提供的最低价格。

## 相关阅读

在我们的用户指南中[设置共享目录的定价和结构](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/define/catalog-shared-pricing-structure.html?lang=zh-Hans)。
