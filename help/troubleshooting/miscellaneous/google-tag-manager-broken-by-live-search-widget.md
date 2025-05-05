---
title: Google Tag Manager已被 [!DNL Live Search] 小组件破坏
description: 本文为 [!DNL Live Search Product Listing Widget] 提供解决方案，以导致 [!DNL Google Tag Manager] 停止运行。
feature: Install, Search, Best Practices
role: Admin, Developer
exl-id: 485f8ccb-cba2-4785-a8e1-a1e98c88b21e
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '98'
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

* 我们的Adobe Commerce Live Search文档中的[[!DNL Live Search] 指南概述](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/guide-overview.html?lang=zh-Hans)

* 在我们的Adobe Commerce Live Search文档中[正在安装 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hans)
