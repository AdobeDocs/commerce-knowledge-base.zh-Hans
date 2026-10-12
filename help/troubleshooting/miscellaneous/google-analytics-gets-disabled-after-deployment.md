---
title: Google Analytics在部署后将被禁用
description: 本主题将讨论您在部署期间可能遇到的Google Analytics典型问题的解决方案。
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: adedf3b3-e153-47a3-ae73-b5d65067b544
    internal-label: Build system
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%
---
# Google Analytics在部署后将被禁用

本主题将讨论您在部署期间可能遇到的Google Analytics典型问题的解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

跨环境部署代码时，生成和部署脚本会验证是否部署了`master/production/staging`分支以启用Google Analytics。 在部署主环境的开发（或子）分支到开发人员环境（集成）时，部署脚本将禁用Google Analytics。

## 原因

此功能旨在确保开发人员的数据和交互不会发送到Google Analytics，也不会由进行跟踪。

## 解决方案

如果要始终启用Google Analytics，请按照开发人员文档中的[部署变量](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics)中的说明设置部署变量`ENABLE_GOOGLE_ANALYTICS = true`。

>[!NOTE]
>
>我们知道，本文可能仍然包含行业标准的软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。
