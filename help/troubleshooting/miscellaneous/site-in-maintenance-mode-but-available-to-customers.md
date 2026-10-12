---
title: 处于维护模式但可供客户使用的站点
description: 本文修复了在启用维护模式（云基础架构上的Adobe Commerce问题）但店面仍对客户可用的情况。
exl-id: 61b81fbd-a382-44b5-94e9-5b6d72f11349
feature: Cache
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '159'
ht-degree: 0%
---
# 处于维护模式但可供客户使用的站点

本文修复了在启用维护模式（云基础架构上的Adobe Commerce问题）但店面仍对客户可用的情况。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本）

## 问题

<u>要再现的步骤：</u>

1. 启用站点的维护模式。
1. 导航到店面。

<u>预期结果：</u>

将显示维护页面。

<u>实际结果：</u>

店面页面照常显示。

## 原因

页面仍会被缓存，因此维护页面不会显示。

## 尽管处于维护模式，站点解决方案仍可见

1. 通过SSH连接到环境。
1. 运行`php bin/magento cache:clean`命令。

## 相关阅读

在开发人员文档中[启用或禁用维护模式](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。
