---
title: 导入时未更新捆绑选项顺序
description: 本文为解决以下问题提供了解决方案：在从.csv文件导入产品后，捆绑包产品选项的显示顺序与它们在导入文件中列出的顺序不同。
exl-id: 7f7bf782-4b35-4067-aa94-417097079f1f
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 导入时未更新捆绑选项顺序

本文为解决以下问题提供了解决方案：在从.csv文件导入产品后，捆绑包产品选项的显示顺序与它们在导入文件中列出的顺序不同。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x
* Magento Open Source

## 问题

<u>先决条件</u>：

您有一个包含捆绑销售产品的有效.csv文件。

<u>重现步骤</u>：

1. 使用[导入功能](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/data-transfer/import/data-import)导入文件。
1. 打开捆绑包产品页面。

<u>预期的结果</u>：

选项顺序与.csv文件中的顺序相同。

<u>实际结果</u>：

选项顺序与.csv文件中的选项顺序不同。

## 原因

未显式声明选项位置。

## 解决方案

1. 为.csv文件中`bundle_values`列的`position`参数中的每个选项显式声明位置。 有关详细说明，请参阅用户指南中的[编辑产品数据](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products#method-2-edit-the-product-data)。
1. 重复导入操作。

有关导入的一般信息，请参阅用户指南中的[导入捆绑包产品](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/data-transfer/examples/data-transfer-bundle-products)。
