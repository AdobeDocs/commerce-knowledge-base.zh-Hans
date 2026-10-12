---
title: 计划内容暂存更新未与过时的Fastly缓存一起显示
description: 本文修复了在使用Content Staging和Fastly时Adobe Commerce存储不显示计划更新的问题。 问题是由于默认启用了Fastly软清除。 此功能可减少应用程序资源负载，并且仅在第二次请求时重新生成新的缓存。 要解决此问题，您可以通过CMS管理员启用清除Commerce页面，以始终重新生成并提供最新内容。
exl-id: becbffaa-b6dd-4e9b-894e-17901c40223a
feature: CMS, Cache, Page Content, Staging
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
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
source-wordcount: '491'
ht-degree: 0%
---
# 计划内容暂存更新未与过时的Fastly缓存一起显示

本文修复了在使用Content Staging和Fastly时Adobe Commerce存储不显示计划更新的问题。 问题是由于默认启用了Fastly软清除。 此功能可减少应用程序资源负载，并且仅在第二次请求时重新生成新的缓存。 要解决此问题，您可以通过CMS管理员启用清除Commerce页面，以始终重新生成并提供最新内容。

## 问题

商店内容资产（页面、产品、块等）的计划更新 更新开始时间后不会立即在店面显示。 如果已使用[内容暂存](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)功能计划了更新，则会发生这种情况。

## 原因

由于Fastly的软清除功能（默认启用），在向Fastly发送&#x200B;**第一个**&#x200B;更新资源的请求时，Adobe Commerce店面仍会收到旧（过时）的缓存内容。 Fastly需要第二个请求来重新生成站点数据。

因此，在第二次请求更新内容之前，Fastly可能会提供过时的内容。

**预期缓存：**&#x200B;使用Content Staging为内容资源计划更新后，Adobe Commerce会发送请求以将缓存更新到Fastly。 Fastly使之前缓存的内容失效（不删除内容）并开始提供更新的内容。

**实际缓存：**&#x200B;如果Fastly在收到&#x200B;**对更新内容的第一个**&#x200B;请求时仍提供过时内容，则它仅在收到&#x200B;**第二个**&#x200B;请求后才会发送重新生成的、正确的内容。 实施此行为是为了减少服务器负载，方法是：仅在具有已验证流量的区域续订缓存，而不重新生成整个网站的缓存。 Fastly逐步更新缓存，节省了应用程序资源。

## 解决方案

如果提供过时内容而不接受第一次请求，则可以禁用软清除并启用清除CMS页面：

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
