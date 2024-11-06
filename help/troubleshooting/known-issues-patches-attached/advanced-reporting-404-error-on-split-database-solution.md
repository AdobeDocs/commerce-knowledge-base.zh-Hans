---
title: 拆分数据库解决方案的高级报告404错误
description: 本文为具有[拆分数据库解决方案](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)的Adobe Commerce 2.3.x用户提供了一个修补程序，该程序在尝试使用高级报表时遇到404错误。
exl-id: b81d4ada-5f38-4882-bc5b-ab4ccd63fc5f
feature: Commerce Intelligence
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# 拆分数据库解决方案的高级报告404错误

本文为具有[拆分数据库解决方案](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)的Adobe Commerce 2.3.x用户提供了一个修补程序，该解决方案在尝试使用高级报表时遇到404错误。

## 受影响的产品和版本

Adobe Commerce 2.3.0 - 2.3.5-p1

## 问题

该修补程序修复了使用错误连接名称收集引号数据的问题。 由于使用的连接名称错误，报价数据不会发送到Magento Business Intelligence (MBI)，并且无法生成报告。

## 解决方案

应用本文中提供的[patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)。

## Patch

该修补程序已附加到本文。 要下载它，请单击以下链接：

[MDVA-26831\_EE\_2.3.4\_v1.composer.patch](assets/MDVA-26831_EE_2.3.4_v1.composer.patch.zip)

## 如何应用修补程序

解压缩文件并按照[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序中的说明操作。
