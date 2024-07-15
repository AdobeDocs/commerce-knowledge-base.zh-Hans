---
title: 'Adobe Commerce 2.3.6：在地址保存时显示无穷无尽的回旋'
description: 本文介绍了一个已知的Adobe Commerce 2.3.6问题，该问题会在店面的“我的帐户”中保存地址时，无限期地显示等待时间微调按钮。
exl-id: 63841114-167e-4915-b6ed-ee0ef4eae36e
feature: Shipping/Delivery, Orders, Checkout
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Adobe Commerce 2.3.6：在地址保存时显示无休止的回旋

本文介绍了一个已知的Adobe Commerce 2.3.6问题，该问题会在店面的“我的帐户”中保存地址时，无限期地显示等待时间微调按钮。

## 受影响的产品和版本

* 启用了顶点集成的Adobe Commerce 2.3.6（仅限Firefox浏览器）

## 问题

在店面的“我的帐户”部分中保存地址时，有时由于“顶点”核心JS中的错误，会无限期地显示正在等待的Spinner。

## 解决方法

解决方法：使用Firefox的替代浏览器。

已在Adobe Commerce 2.3.1中修复此问题。

## 相关阅读

* [在我们的支持知识库中使用VertexAddress Cleansing](/help/troubleshooting/miscellaneous/vertex-address-cleansing-different-addresses-not-allowed.md)取消选择“我的帐单和送货地址相同”时，不允许使用不同的地址。
* 在我们的支持知识库中更新[Adobe Commerce 2.4.1顶点地址验证消息](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md)。
