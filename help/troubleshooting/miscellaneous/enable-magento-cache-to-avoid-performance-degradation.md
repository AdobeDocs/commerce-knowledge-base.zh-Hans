---
title: 启用缓存以避免性能下降
description: 本文介绍如何解决因禁用某些Adobe Commerce缓存类型而导致的网站速度缓慢问题。
exl-id: e4e5a753-efa3-4552-aaf6-28e44efcfa5b
feature: Cache, Observability
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# 启用缓存以避免性能下降

本文介绍如何解决因禁用某些Adobe Commerce缓存类型而导致的网站速度缓慢问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x

## 问题

您注意到性能下降。 例如，“结帐”页面加载缓慢，或New Relic中的Apdex值下降。

## 原因

性能下降的一个原因可能是某些Adobe Commerce缓存类型被禁用。

## 解决方案

1. 首先，检查Adobe Commerce缓存的状态，看看这是否是问题所在。 为此，请[SSH到您的环境](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh)并运行以下命令：

   ```bash
   php bin/magento cache:status
   ```

   这将显示每种缓存类型的状态（禁用时为“0”，启用时为“1”）。 或者，您可以在`app/etc/env.php`文件中获取此信息。

1. 调查已禁用的高速缓存类型。 所有Adobe Commerce缓存类型都应启用，除非您从Adobe收到了其他指导。 第三方扩展不得要求禁用Adobe Commerce缓存。
1. 如果调查确认某些缓存类型被错误地禁用，请通过为每个缓存类型运行以下命令来启用它们： `php bin/magento cache:enable <your_disabled_cache_type>`

如果存在可以或应该禁用特定Adobe Commerce缓存类型的顾虑和/或问题，请[联系Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)以寻求建议。

## 相关阅读

我们开发人员文档中的Adobe Commerce缓存文档：

* [Adobe Commerce缓存概述](https://developer.adobe.com/commerce/frontend-core/guide/caching/)
* [管理缓存](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-cache)

出现性能问题的其他可能原因以及解决方案：

* [禁用Adobe Commerce横幅输出以提高网站性能](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909)
* [MySQL表太大](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26945)
* [性能缓慢、运行速度缓慢且运行时间较长](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)