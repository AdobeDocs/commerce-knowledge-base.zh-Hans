---
title: 无法保存实体Adobe Commerce后端
description: 本文提供一种解决方案，用于解决您无法在Adobe Commerce后端中保存实体的问题。 例如，当您无法编辑和保存特定“cart_price”规则时。
exl-id: e45dc88a-2da0-4524-bd61-6634cfebb169
feature: Admin Workspace, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 无法保存实体Adobe Commerce后端

本文提供一种解决方案，用于解决您无法在Adobe Commerce后端中保存实体的问题。 例如，当您无法编辑和保存特定`cart_price`规则时。

## 受影响的产品和版本

此问题可能会影响已配置最大会话大小的所有Adobe Commerce版本。 从Magento Open Source2.3.7 - p1和Adobe商务（所有部署方法）2.4.3开始添加此项。


## 问题

当您尝试重新配置商店时，页面会重新加载，并且您的更改不会保存。 在`var/log/system.log`中可以看到消息：

*[2021-11-27 00:30:52]报告。警告： 418056的会话大小超过了允许的会话最大大小256000。[][]*

<u>重现步骤</u>：

未保存存储配置的示例：

1. 在Adobe Commerce商店的生产> **营销** > **购物车价格规则**&#x200B;中选择规则。
1. 选择一个规则并设置为&#x200B;*不活动*，然后保存更改。

<u>预期的结果</u>：

规则设置为不活动。

<u>实际结果</u>：

* 页面重新加载，无任何消息。
* 规则仍设置为活动。

## 原因

此问题与最近引入的新功能有关，该功能影响了最大会话大小。 请参阅我们的开发人员文档中的[会话管理](https://docs.magento.com/user-guide/stores/security-session-management.html)。

## 解决方案

增加（**存储** > **配置** > **高级** > **系统** > **安全性** >最大会话大小）中的“最大会话大小”值。

## 相关阅读

* 用户指南中的[营销菜单](https://docs.magento.com/user-guide/marketing/marketing-menu.html)。
