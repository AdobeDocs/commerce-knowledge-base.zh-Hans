---
title: 计划内容暂存更新未与过时的Fastly缓存一起显示
description: 本文修复了在使用Content Staging和Fastly时Adobe Commerce存储不显示计划更新的问题。 问题是由于默认启用了Fastly软清除。 此功能可减少应用程序资源负载，并且仅在第二次请求时重新生成新的缓存。 要解决此问题，您可以通过Commerce管理员启用“清除CMS”页面，以便始终重新生成并提供最新内容。
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 计划内容暂存更新未与过时的Fastly缓存一起显示

本文修复了在使用Content Staging和Fastly时Adobe Commerce存储不显示计划更新的问题。 问题是由于默认启用了Fastly软清除。 此功能可减少应用程序资源负载，并且仅在第二次请求时重新生成新的缓存。 要解决此问题，您可以通过Commerce管理员启用“清除CMS”页面，以便始终重新生成并提供最新内容。

## 问题

商店内容资产（页面、产品、块等）的计划更新 更新开始时间后不会立即在店面显示。 如果已使用[内容暂存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)功能计划了更新，则会发生这种情况。

## 原因

由于Fastly的软清除功能（默认启用），在向Fastly发送&#x200B;**第一个**&#x200B;更新资源的请求时，Adobe Commerce店面仍会收到旧（过时）的缓存内容。 Fastly需要第二个请求来重新生成站点数据。

因此，在第二次请求更新内容之前，Fastly可能会提供过时的内容。

**预期缓存：**&#x200B;使用Content Staging为内容资源计划更新后，Adobe Commerce会发送请求以将缓存更新到Fastly。 Fastly使之前缓存的内容失效（不删除内容）并开始提供更新的内容。

**实际缓存：**&#x200B;如果Fastly在收到&#x200B;**对更新内容的第一个**&#x200B;请求时仍提供过时内容，则它仅在收到&#x200B;**第二个**&#x200B;请求后才会发送重新生成的、正确的内容。 实施此行为是为了减少服务器负载，方法是：仅在具有已验证流量的区域续订缓存，而不重新生成整个网站的缓存。 Fastly逐步更新缓存，节省了应用程序资源。

## 解决方案

如果提供过时内容（即使为第一个请求提供）是不可接受的，则可以禁用软清除并启用清除CMS页面：

1. 以管理员身份登录到您的本地Commerce管理员。
1. 转到&#x200B;**商店** > **配置** > **高级** > **系统** > **全页缓存**。
1. 展开&#x200B;**Fastly配置**，然后展开&#x200B;**高级**。
1. 将&#x200B;**使用软清除**&#x200B;设置为&#x200B;*否*。
1. 将&#x200B;**清除CMS页面**&#x200B;设置为&#x200B;*是*。
1. 单击页面顶部的&#x200B;**保存配置**。


![purge_options.png](assets/purge_options.png)

## 相关文档

* 在《云基础架构上的Commerce指南》中[配置清除选项](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)。
* 内容和设计文档中的[内容暂存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)。
* 在Fastly文档中[提供过时的内容](https://docs.fastly.com/guides/performance-tuning/serving-stale-content)。
