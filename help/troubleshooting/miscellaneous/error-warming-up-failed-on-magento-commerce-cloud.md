---
title: 错误：在云基础架构上的Adobe Commerce上预热失败
description: 本文为页面缓存预热并失败并出现错误提供了解决方案：
exl-id: 20a88030-b1c9-4fdc-83c1-f344d44cd2e1
feature: Cache, Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '213'
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
