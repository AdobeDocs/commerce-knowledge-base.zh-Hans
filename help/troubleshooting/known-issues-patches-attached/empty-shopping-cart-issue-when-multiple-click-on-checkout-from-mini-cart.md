---
title: 多次单击从迷你购物车结帐时出现空购物车问题
description: 针对与迷你购物车中客户多次单击**转到结帐**后购物车为空相关的已知Adobe Commerce 2.2.3问题，本文提供了一个修补程序。
exl-id: 06b82c91-8998-4e7b-9fc0-671c9b2a2d3f
feature: Checkout, Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# 多次单击从迷你购物车结帐时出现空购物车问题

针对与迷你购物车中客户多次单击&#x200B;**转到结帐**&#x200B;后购物车为空相关的已知Adobe Commerce 2.2.3问题，本文提供了一个修补程序。

## 问题

客户将产品添加到购物车，尝试通过多次单击&#x200B;**转到结帐**&#x200B;按钮来结帐，但是当他们转到购物车时，购物车是空的。 迷你购物车可能仍会显示产品。

<u>重现问题的步骤</u> ：

1. 在商店正面打开产品页面。
1. 将产品添加到购物车。
1. 在迷你购物车中，单击&#x200B;**转到结帐**&#x200B;多次。

<u>预期的结果</u> ：

购物车包含您已添加的所有产品。

<u>实际结果</u> ：

您的购物车中没有任何项目。

## Patch

修补程序已附加到本文。 要下载补丁程序，请向下滚动到文章末尾，然后单击所需的文件名或单击以下链接之一：

[下载MDVA-10441\_EE\_2.2.3\_v3.composer.patch](assets/MDVA-10441_EE_2.2.3_v3.composer.patch.zip)

[下载MDVA-17078\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-17078_EE_2.2.5_COMPOSER_v1.patch.zip)

### 兼容的Adobe Commerce版本

修补程序是为以下对象创建的：

* Adobe Commerce内部部署2.2.3（`MDVA-10441_EE_2.2.3_v3.composer.patch`文件）
* 云基础架构2.2.5上的Adobe Commerce （`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch`文件）

`MDVA-10441_EE_2.2.3_v3.composer.patch`修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 从2.2.1到2.2.5的Adobe Commerce on cloud基础架构版本
* 从2.2.1到2.2.5的Adobe Commerce本地版本

`MDVA-17078_EE_2.2.5_COMPOSER_v1.patch`修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce 2.2.5

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
