---
title: 在Adobe Commerce 2.4.x中无法进行精确匹配搜索
description: 本文澄清了Adobe Commerce 2.4.x中使用同一搜索字符串的存储前端搜索结果与Adobe Commerce 2.3.x不同的问题。
exl-id: 0867558e-1d74-4b83-abf3-651ca7fc32cb
feature: Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 在Adobe Commerce 2.4.x中无法进行精确匹配搜索

本文澄清了Adobe Commerce 2.4.x中使用同一搜索字符串的存储前端搜索结果与Adobe Commerce 2.3.x不同的问题。

## 受影响的产品和版本

- Adobe Commerce（所有部署方法）2.4.x、2.3.x
- 实时搜索

## 问题

<u>先决条件：</u>

在Adobe Commerce 2.3和Adobe Commerce 2.4商店中，您都有属性值为`Saga 1`和`Saga 16`的产品。

<u>要再现的步骤：</u>

1. 在Adobe Commerce 2.3支持的商店前面，在搜索字段中输入&#x200B;*Saga 1*，然后单击&#x200B;**搜索**。
1. 请注意，在搜索结果中，您只能获得属性值为`Saga 1`的产品。
1. 在Adobe Commerce 2.4支持的商店前面，在搜索字段中输入&#x200B;*Saga 1*，然后单击&#x200B;**搜索**。

<u>实际结果：</u>

2.4中的搜索结果包含具有属性值`Saga 1`和`Saga 16`的产品。

<u>预期结果：</u>

2.4中的搜索结果与2.3类似，仅包含属性值`Saga 1`的产品。

## 原因

2.3.x中使用的Adobe Commerce本机搜索功能提供了完全匹配的搜索结果。 虽然随Adobe Commerce 2.4.x一起发布的可供安装的可选模块Live Search的实施方式不同，但实际结果是使用该模块时的预期行为。

## 相关阅读

在我们的用户指南中[安装实时搜索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)。

在开发人员文档中[实时搜索](https://devdocs.magento.com/live-search/overview.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=Live%20Search)。
