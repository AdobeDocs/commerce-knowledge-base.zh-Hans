---
title: 在Adobe Commerce上的群集中查看环境vCPU层
promoted: true
description: 本文介绍如何使用“Adobe Commerce观察”上的“New Relic基础架构”选项卡检查您的vCPU层分配。 Adobe Commerce观察信息是一个New Relic Nerdlet，它显示Adobe Commerce站点的状态、当前和过去的时间视图。
exl-id: a0332e7e-d38d-47d3-b3da-293902f45edc
source-git-commit: 309fda5284de3b8be54e95bf2bfd8ff1777b6c90
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# 在Adobe Commerce上的群集中查看环境vCPU层

本文介绍如何使用“Adobe Commerce观察”上的“New Relic基础架构”选项卡检查您的vCPU层分配。 Adobe Commerce观察信息是一个New Relic Nerdlet，它显示Adobe Commerce站点的状态、当前和过去的时间视图。

## 受影响的产品和版本：

云基础架构上的Adobe Commerce 2.4.3 - 2.4.6

## 通过观察检查Adobe Commerce的vCPU层分配：

要访问并登录到Adobe Commerce Nerdlet的New Relic观察，请执行以下操作：

1. 从New Relic主页中，单击&#x200B;**应用程序**。
1. 单击Adobe Commerce的&#x200B;**观察**。
1. 此时将打开Adobe Commerce Nerdlet的观察结果。
1. 单击&#x200B;**选择帐户**&#x200B;下拉列表并选择帐户。
1. 您可以填写项目ID、New Relic帐号或帐户名称，或者浏览帐户列表。
1. 单击带有时钟图标的浅蓝色下拉菜单（朝向Nerdlet窗口的右上角）。
1. 如果您正在尝试确定事件/问题的原因，请选择票证日期和时间之前的时间，以查看是否存在任何以前的事件/数据。 您可以使用预设的时间范围，或通过选择&#x200B;**设置自定义**&#x200B;来设置自定义时间范围。
1. 在选项卡上，单击&#x200B;**基础架构**。 有三个vCPU层图：
   * 第一个图形显示时间线上&#x200B;**vCPU层视图大于2周（您需要选择大于2周的时间线）。 注意：采样率将为每天。 如果群集在一天内发生上传/下传，则结束层大小将在第二天**&#x200B;显示。
   * 第二个图形显示时间线上的&#x200B;**vCPU层视图（需要选择大于24小时但不大于2周的时间线）**。
   * 第三个图形显示时间线上的&#x200B;**vCPU层视图（按节点），应查看时间线小于24小时**。

## 相关阅读

* 在我们的支持知识库中对Adobe Commerce概述[的观察](/help/support-tools/observation-for-adobe-commerce/observation-adobe-commerce-overview.md)。
