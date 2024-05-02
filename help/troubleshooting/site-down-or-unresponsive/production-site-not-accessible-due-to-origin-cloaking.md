---
title: 由于源遮蔽，无法访问站点
description: 本文为云基础架构暂存或生产站点店面和/或管理员无法访问您的Adobe Commerce时提供了一个解决方案。
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# 由于源遮蔽，无法访问站点

本文为云基础架构暂存或生产站点店面和/或管理员无法访问您的Adobe Commerce时提供了一个解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.x、2.4.x

## 问题

https：/&#x200B;/mydomain.com.c.&lt;projectid>无法再访问.magento.cloud/。

<u>重现问题的步骤：</u>

1. 登录到您的项目。
1. 单击 **访问项目** URL和SSH的列表。

<u>实际结果：</u>

页面加载失败，并出现以下错误：

*NET：：ERR\_CERT\_INVALID*  *TLS警报，错误证书(554)：*

<u>预期结果：</u>

页面加载成功。

## 原因

源遮盖已启用，因此源不再可直接访问。

源遮蔽是一项安全功能，允许Adobe Commerce阻止任何流向云基础架构（源）的非快速通信以防止DDoS攻击。

## 解决方案

* 如果您的云站点处于活动状态，请切换到https://mydomain.com/。
* 如果您有一个活动站点（非云），请使用https://mydomain.com/域设置一个子域 `mcprod.mydomain.com` 并更新 **基本URL** 到 *https://mcprod.mydomain.com* 相反，则 [将DNS指向Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#update-dns-configuration-with-development-settings).

## 相关阅读

[Fastly Origin遮盖功能启用常见问题解答](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) 在我们的支持知识库中。
