---
title: 'Adobe Commerce 2.3.6、2.4.0-p1、2.4.1已知问题：dotdigital登录'
description: 本文介绍了一个Adobe Commerce 2.3.6、2.4.0-p1和2.4.1已知问题，即在启用dotdigital帐户的情况下，无法通过Admin Panel登录[dotdigital](https://dotdigital.com/)。
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Adobe Commerce 2.3.6、2.4.0-p1、2.4.1已知问题： dotdigital login

本文介绍了一个Adobe Commerce 2.3.6、2.4.0-p1和2.4.1已知问题，其中在启用dotdigital帐户的情况下，无法通过Admin Panel登录到[dotdigital](https://dotdigital.com/)。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.6（仅限Safari浏览器）
* 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.4.0-p1（仅限Safari浏览器）
* 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.4.1（仅限Safari浏览器）

## 问题

<u>先决条件</u>：

1. dotdigital帐户存在。
1. Adobe Commerce中存在有效的dotdigital API凭据。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **配置** > **DOTDIGITAL** > **聊天设置** > **已启用**&#x200B;设置为&#x200B;*是。*
1. 单击&#x200B;**配置聊天小组件**&#x200B;中的&#x200B;**配置**&#x200B;或&#x200B;**配置聊天团队**。

<u>预期的结果</u>：

应通过管理员面板成功打开聊天设置页面。

<u>实际结果</u>：

无法登录到dotdigital。

## 解决方案

解决方法：对此特定情况使用Safari的替代浏览器。

## 相关阅读

[Adobe Commerce 2.4.1已知问题 — 在我们的支持知识库中，无法使用其他送货/帐单地址验证顶点地址](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md)。
