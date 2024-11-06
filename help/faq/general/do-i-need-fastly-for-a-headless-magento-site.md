---
title: 我是否需要Fastly才能使用Headless Adobe Commerce网站？
description: 我是否需要Fastly才能使用Headless Adobe Commerce网站？
exl-id: d7e07160-6a61-4c03-8f8c-4f879d86ea44
feature: Cache, GraphQL, Compliance
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 我是否需要Fastly才能使用Headless Adobe Commerce网站？

>[!NOTE]
>
>所有客户必须将Fastly用于其生产和暂存环境。 Fastly是一个内容交付网络(CDN)，在云基础架构项目上作为Adobe Commerce的一部分提供完整页面缓存、图像优化和安全服务(DDoS和WAF)。 这些是Adobe Commerce解决方案的核心组件，可提高性能和安全性。 这些功能是AdobePCI合规性的一部分。 您必须在Starter Master、Staging、Pro Staging和Production环境中设置这些Fastly服务。 如果您在Headless部署中使用Adobe Commerce，则来自公共Internet的所有API流量都必须通过Fastly，我们强烈建议您使用Fastly缓存GraphQL响应。 请参阅我们的开发人员文档中的[GraphQL Developer Guide > Caching with Fastly](https://developer.adobe.com/commerce/webapi/graphql/usage/caching/#caching-with-fastly)。

## **问题**

我正在开发Adobe Commerce的Headless实施。 我是否需要将Fastly用作CDN服务？

## **答案**

不，你没有。在这种情况下，您可以跳过使用Fastly — 至少在开发开始时是这样。

您可能不想启用的唯一情况是Headless部署。
请参阅我们的开发人员文档中的[Adobe Commerce云> Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)。

不过，最有可能的是，您需要Fastly才能使用其SSL证书。

作为云订阅计划的一部分，所有Adobe Commerce云基础架构客户都将从Fastly获取共享SSL证书。 将自己的SSL证书添加到Fastly是一个单独的、相当昂贵的付费选项。 因此，我们强烈建议启用Fastly，并且至少在上线前在暂存和生产环境中测试它，即使对于您的headless Adobe Commerce网站也是如此。

## 更多信息

* [Headless网站：分离式架构有什么大不了的？由[Josh Koenig](https://pantheon.io/team/josh-koenig)进行的](https://pantheon.io/blog/headless-websites-whats-big-deal-decoupled-architecture)。
* 在我们的开发人员文档中[Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly)。
