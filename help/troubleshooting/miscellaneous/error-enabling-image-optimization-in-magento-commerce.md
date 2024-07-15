---
title: 在Adobe Commerce中启用图像优化时出错
description: 本文为默认情况下禁用Fastly图像优化(IO)时的问题提供了解决方案，并通知联系Fastly以启用图像优化。 （Fastly Cloud Image Optimizer是一种实时图像操作和优化服务，通过提供带宽高效的图像来加快图像交付。）
exl-id: 7b64c786-3c74-4642-b0d0-15b5648163a0
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# 在Adobe Commerce中启用图像优化时出错

本文为默认情况下禁用Fastly图像优化(IO)时的问题提供了解决方案，并通知联系Fastly以启用图像优化。 （Fastly Cloud Image Optimizer是一种实时图像操作和优化服务，通过提供带宽高效的图像来加快图像交付。）

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x

## 问题

在Fastly配置页面的Fastly IO代码片段旁边，您可以看到当前状态： \_disabled \_并在下面显示以下消息：请联系您的销售代表或向`support@fastly.com`发送电子邮件，以请求为您的Fastly服务激活图像优化。

## 原因

该站点可能尚未上线。 当网站在Fastly数据库中上线时，有一些流程可用于预加载网站。

## 解决方案

创建[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)并请求图像优化。
