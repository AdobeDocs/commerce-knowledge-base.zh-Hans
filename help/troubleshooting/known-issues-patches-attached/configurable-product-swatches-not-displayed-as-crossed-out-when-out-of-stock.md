---
title: 缺货时未显示的可配置产品样本被划掉
description: 本文为已知的Adobe Commerce 2.2.2问题提供了一个补丁，该问题与可配置产品样本在店面中不显示为交叉缺货有关。
exl-id: 79c59a3f-a94b-4726-8af1-5fe754ea95a5
feature: Configuration, Orders, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# 缺货时未显示的可配置产品样本被划掉

本文为已知的Adobe Commerce 2.2.2问题提供了一个补丁，该问题与可配置产品样本在店面中不显示为交叉缺货有关。

## 问题

当您拥有可配置产品时，对于特定选项组合，相关的简单产品缺货，样本仍然可用，并且可以在店面中选择。

<u>重现步骤</u>：

1. 在Commerce Admin中，使用两个属性的选项创建可配置产品：颜色（红色、黑色）和大小(S、M、L)。
1. 将每个相应的简单产品的数量设置为“1”。
1. 在店面，将红色的M产品添加到购物车和结账。
1. 在管理员中，处理订单，以便将物料数量更新为“0”。
1. 确保不允许延交订单。
1. 在店面，导航到相同的产品页面并选择相同的选项：红色、M。

<u>预期的结果</u>：

红色的M色板具有红色斜杠，无法选择。

<u>实际结果</u>：

可以选择红色的M色板。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-8215\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-8215_EE_2.2.2_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce（所有部署方法） 2.2.2

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.2.0-2.2.3

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
