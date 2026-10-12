---
title: Google Tag Manager已被[!DNL Live Search]小组件破坏
description: 本文为[!DNL Live Search Product Listing Widget]提供了一个解决方案，导致[!DNL Google Tag Manager]停止运行。
feature: Install, Search, Best Practices
role: Admin, Developer
exl-id: 485f8ccb-cba2-4785-a8e1-a1e98c88b21e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%
---
# [!DNL Google Tag Manager]被[!DNL Live Search]小组件破坏

本文为[!DNL Live Search Product Listing Widget]提供了一个解决方案，导致[!DNL Google Tag Manager]停止运行。

## 受影响的产品和版本

* Adobe Commerce版本2.4.4 - 2.4.6-p2

## 问题

[!DNL Live Search Product Listing Widget]导致[!DNL Google Tag Manager]停止运行。

## 解决方案

要确保[!DNL Google Tag Manager]可与[!DNL Live Search]一起使用，请使用&#x200B;*搜索适配器*。

为此，请在管理员中禁用该构件。 [!DNL Live Search]然后默认为使用&#x200B;*搜索适配器*。

## 相关阅读

* 我们的Adobe Commerce Live Search文档中的[[!DNL Live Search] 指南概述](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html)

* 在我们的Adobe Commerce Live Search文档中[正在安装 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)
