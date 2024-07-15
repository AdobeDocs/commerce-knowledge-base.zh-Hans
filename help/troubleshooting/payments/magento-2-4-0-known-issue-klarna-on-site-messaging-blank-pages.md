---
title: 'Adobe Commerce 2.4.0已知问题：Klarna现场消息传送空白页'
description: 本文介绍了与Klarna支付方法有关的一个已知的Adobe Commerce 2.4.0问题，该问题导致在启用现场消息传送时没有指定设计主题，从而导致店面无法正确显示产品页面（产品页面显示为空白）。
exl-id: f0f9edfc-eaad-4947-9200-41e217bfbe84
feature: Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Adobe Commerce 2.4.0已知问题： Klarna现场消息传递空白页

本文介绍了与Klarna支付方法有关的一个已知的Adobe Commerce 2.4.0问题，该问题导致在启用现场消息传送时没有指定设计主题，从而导致店面无法正确显示产品页面（产品页面显示为空白）。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

<u>先决条件：</u>已启用Klarna付款方法。

<u>要再现的步骤：</u>

1. 在Commerce Admin中，转到&#x200B;**商店** > **配置** > **销售** > **付款方式** > **Klarna** > **Klarna现场消息**。
1. 将&#x200B;**启用**&#x200B;设置为&#x200B;*是*。
1. 将&#x200B;**设计主题**&#x200B;字段留空。
1. 单击&#x200B;**保存配置**&#x200B;以保存配置。
1. 转到店面并导航到任何产品页面。

<u>预期结果：</u>

页面加载成功，默认设计主题应用于Klarna现场消息传递。

<u>实际结果：</u>

此时将显示空白页。

## 解决方案

如果启用Klarna现场消息传递，请始终确保&#x200B;**设计主题**&#x200B;字段不为空。
