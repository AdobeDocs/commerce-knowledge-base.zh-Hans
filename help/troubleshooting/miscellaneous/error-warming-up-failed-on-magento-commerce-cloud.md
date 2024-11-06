---
title: '错误：在云基础架构上的Adobe Commerce上预热失败'
description: '本文为页面缓存预热并失败并出现错误提供了解决方案：'
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 错误：在云基础架构上的Adobe Commerce上预热失败

本文为页面缓存预热并失败并出现错误提供了解决方案：

*错误：预热失败：`<website link>`*

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

缓存预热失败。

<u>重现步骤</u>：

启动缓存预热操作。

<u>预期的结果</u>：

页面或整个网站加载。

<u>实际结果</u>：

站点不可用或响应时间太长。 *错误：预热失败：`<website link>`*

## 原因

在启用HTTP访问控制的情况下，缓存预热不起作用。

## 解决方案

请确保未启用访问控制：转到特定分支/环境并单击&#x200B;**设置**&#x200B;图标，然后选中&#x200B;**HTTP访问控制**&#x200B;设置 — 在此情况下无法发生缓存预热问题，必须禁用访问控制。

## 相关阅读

* 我们的用户指南中的[Adobe Commerce用户指南>全页缓存](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching)。
* 在我们支持知识库的Adobe Commerce](/help/troubleshooting/miscellaneous/cache-warming-up-and-site-unavailable-on-magento.md)上，[缓存预热和网站不可用。
