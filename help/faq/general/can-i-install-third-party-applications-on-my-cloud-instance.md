---
title: 我可以在我的云实例上安装第三方应用程序吗？
description: 不适用。 不允许在Adobe Commerce上的云基础架构服务器上安装第三方应用程序（如WordPress或Drupal）。 您必须在外部服务器上托管此类应用程序。
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# 我可以在我的云实例上安装第三方应用程序吗？

不适用。 不允许在Adobe Commerce上的云基础架构服务器上安装第三方应用程序（如WordPress或Drupal）。 您必须在外部服务器上托管此类应用程序。

## 原因

### 服务条款协议

Adobe Commerce on cloud infrastructure Edition [服务条款协议](https://magento.com/legal/terms/cloud-terms)在第18条中声明以下内容：

> 客户同意，Adobe Commerce和服务将不用于托管不直接依赖于本软件的其他第三方软件应用程序。

作为云解决方案，Adobe对服务器的安全承担全部责任。 为确保高安全性，我们仅允许在专用云服务器上托管Adobe Commerce应用程序。

### PCI合规性

作为PCI认证的第1级解决方案提供商，云基础架构上的Adobe Commerce必须遵循PCI数据安全标准，并确保：

>...开发和维护安全的系统和应用程序
> （[Adobe的PCI合规性方法](https://magento.com/pci-compliance)要求6，维护漏洞管理计划）

由于Adobe无法保证第三方应用程序的PCI合规性，因此不允许在云服务器上安装此类应用程序。

## 提示：使用Commerce Marketplace扩展实现更好的集成

为了改进云基础架构应用程序上的Adobe Commerce与托管在外部服务器上的第三方解决方案的集成，我们建议您使用可能适合您用途的[Commerce Marketplace](https://marketplace.magento.com)扩展。
