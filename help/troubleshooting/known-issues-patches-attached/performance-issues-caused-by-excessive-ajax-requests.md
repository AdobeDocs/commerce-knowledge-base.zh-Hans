---
title: 过多Ajax请求导致的性能问题
description: 本文为过度的Ajax请求导致的已知Adobe Commerce性能问题提供了一个修补程序。 已在Adobe Commerce 2.3.4中修复此问题。
exl-id: d9a69406-3970-4556-aa6a-1309b24366d8
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# 过多Ajax请求导致的性能问题

本文为过度的Ajax请求导致的已知Adobe Commerce性能问题提供了一个修补程序。 已在Adobe Commerce 2.3.4中修复此问题。

## 问题

Adobe Commerce可能从店面向服务器发送冗余[Ajax请求](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md)，以获取横幅信息和客户信息。 这些Ajax请求会对性能产生影响，尤其是在高负载（高容量和高流量）情况下。 因此，如果未使用横幅功能，建议您完全[禁用Adobe Commerce横幅模块输出](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md)并应用修补程序以改进客户信息检索。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-24597\_EE\_2.2.9\_COMPOSER\_v1.patch](assets/MDVA-24597_EE_2.2.9_COMPOSER_v1.patch.zip)

### 兼容的Adobe Commerce版本

该修补程序适用于以下产品和版本：

* 云基础架构上的Adobe Commerce 2.2.9
* Adobe Commerce内部部署2.2.9

如果您具有不同的版本Adobe Commerce，请考虑更新到最新的2.3.x版本。 如果当前无法执行此操作，请[联系Adobe Commerce支持](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，为您的版本请求修补程序。

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
