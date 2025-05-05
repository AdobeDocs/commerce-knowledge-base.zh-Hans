---
title: 错误 [!DNL opensearch] 搜索引擎不存在。 回退到 [!DNL livesearch]。
description: 本文为您看到错误“Error- [!DNL opensearch] 搜索引擎不存在”的问题提供了解决方案。 回退到 [!DNL livesearch].'，在Adobe Commerce on cloud infrastructure中。
feature: Deploy, Search
role: Developer
exl-id: a6cc981d-b8f0-402d-8771-60d2f21f09f8
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# 错误[!DNL opensearch]搜索引擎不存在。 正在回退到[!DNL livesearch]。

本文为您看到以下错误的问题提供了解决方案： *错误： [!DNL opensearch]搜索引擎不存在。 正在回退到[!DNL livesearch]。在使用[!DNL Live Search]的云基础架构上的Adobe Commerce中的*。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本
* [!DNL Live Search]已安装并正在使用中

## 问题

日志中显示以下消息（可在[!DNL New Relic]中观察到）：
*错误： [!DNL opensearch]搜索引擎不存在。 正在回退到[!DNL livesearch].*

## 解决方案

1. 修改`.magento.env.yaml`文件。
1. 找到以下行：

   ```yaml
     deploy:
   ...
       SEARCH_CONFIGURATION:
         engine: opensearch
   ```

1. 如果没有这些行，请将其添加到`.magento.env.yaml`文件。
1. 如果这些行存在，**将引擎**&#x200B;从&#x200B;*[!DNL opensearch]*&#x200B;修改为&#x200B;*[!DNL livesearch]*。
1. 提交更改，然后重新部署。

## 相关阅读

* 在我们的实时搜索指南中[安装 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html?lang=zh-Hans)
