---
title: 双击购物车中的“删除链接”后出现“500错误”
description: 本文为Cloud Infrastructure 2.2.0上已知的Adobe Commerce问题提供了一个修补程序，该问题与客户在尝试删除两次购物车项目（通过双击*Remove*链接或在其他选项卡中单击它）时出现错误有关。
exl-id: 927cf681-febf-42cc-8db5-469bcf8f2012
feature: Orders, Shopping Cart
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# 双击购物车中的“删除链接”后出现“500错误”

本文为Cloud Infrastructure 2.2.0上已知的Adobe Commerce问题提供了一个修补程序，该问题与客户在尝试删除两次购物车项目时出现错误有关（通过双击&#x200B;*删除*&#x200B;链接或在其他选项卡中单击该链接）。

## 问题

当客户双击购物车中的&#x200B;*删除*&#x200B;链接，尝试从购物车中删除产品时，他们会获得一个空白页面，该页面显示以下错误消息： *“此页面无法正常工作。 HTTP错误500。*&#x200B;如果客户使用购物车页面打开两个浏览器选项卡，并首先在一个选项卡中删除产品，然后在第二个选项卡中删除产品，则会发生同样的问题。

<u>重现问题的步骤</u> ：

1. 将产品添加到店面的购物车。
1. 导航到购物车页面。
1. 双击“Remove（删除）”链接。

或者

1. 将产品添加到店面的购物车。
1. 导航到购物车页面。
1. 打开新的浏览器选项卡，然后导航到购物车页面（同一产品）。
1. 从购物车中删除产品。
1. 打开第二个选项卡并再次移除产品。

<u>预期结果</u> ：产品已从购物车中移除，且未出现错误。

<u>实际结果</u> ：产品被删除，错误为： *&quot;此页面无法正常工作。 HTTP错误500“*”错误消息。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-8623\_EE\_2.2.0\_v1.composer.patch](assets/MDVA-8623_EE_2.2.0_v1.composer.patch.zip)

## 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.0

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.2.1 - 2.2.5
* Adobe Commerce内部部署2.2.0 - 2.2.5

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
