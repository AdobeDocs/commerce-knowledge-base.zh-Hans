---
title: 在“管理员”的“订单”网格中不显示订单
description: 本文为已知的Adobe Commerce 2.2.1问题提供了一个修补程序，该问题与Commerce Admin的“订单”网格中不显示的订单有关。
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# 在“管理员”的“订单”网格中不显示订单

本文为已知的Adobe Commerce 2.2.1问题提供了一个修补程序，该问题与Commerce Admin的“订单”网格中不显示的订单有关。

## 问题

在安装了B2B扩展的Adobe Commerce 2.2.1中，由注册客户在店面创建的订单不会显示在Commerce管理员中客户帐户的订单列表中。 在调试日志(`./var/log/debug.log`)中记录了以下错误：

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>先决条件</u>：

您的商店目录包含产品，而不是Adobe Commerce示例数据，并且已安装B2B扩展。

<u>重现步骤</u>：

1. 导航到店面并创建客户帐户。
1. 将产品添加到购物车，完成结帐并提交订单。
1. 登录到管理员。
1. 导航到&#x200B;**客户，**，然后选择&#x200B;**所有客户**。
1. 对于新创建的客户，单击&#x200B;**编辑**。
1. 单击左侧面板中的&#x200B;**订单**。

<u>预期的结果</u>：

最近提交的订单将列在网格中。

<u>实际结果</u>：

不显示“订单”网格。 此时将显示一个空白页面。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-7868\_EE\_2.2.1\_v1\_composer.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce内部部署2.2.1

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 从2.2.0到2.2.3的云基础架构上的Adobe Commerce
* Adobe Commerce内部部署2.2.0和2.2.2到2.2.3

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
