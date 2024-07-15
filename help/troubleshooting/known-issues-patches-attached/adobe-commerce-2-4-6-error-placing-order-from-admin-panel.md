---
title: 从管理员面板下订单时Adobe Commerce 2.4.6出错
description: 当您从Adobe Commerce管理面板下订单后，商店选择变得卡住，针对云基础架构上的已知Commerce 2.4.6问题，本文提供了一个修补程序。
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 从管理员面板下订单时Adobe Commerce 2.4.6出错

当您从Adobe Commerce管理面板下订单后，商店选择变得卡住，针对云基础架构上的已知Commerce 2.4.6问题，本文提供了一个修补程序。

## 问题

从“管理员”面板下订单时，您会卡在商店选择中。

<u>重现步骤</u>

1. 转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;并选择客户以创建订单。
2. 从商店选择器屏幕中选择要下订单的商店。

<u>预期的结果</u>

选择商店后，即可完成订单。

<u>实际结果：</u>

选择商店后，您将被重定向回商店选择器页面，并且无法创建订单。

## Patch

单击以下链接以下载修补程序。

[下载ACSD-52277_2.4.6.patch](assets/ACSD-52277_2.4.6.patch.zip)

### 兼容的Adobe Commerce版本

该补丁是为Adobe Commerce on cloud infrastructure以及Adobe Commerce内部部署2.4.6和2.4.6-p1创建并兼容的。

## 如何应用修补程序

* 有关在云基础架构上应用Adobe Commerce修补程序的说明，请参阅我们的Commerce on Cloud Infrastructure指南中的[应用修补程序](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。
* 有关为Adobe Commerce本地应用修补程序的说明，请参阅《Commerce升级指南》中的[应用修补程序](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer)。
