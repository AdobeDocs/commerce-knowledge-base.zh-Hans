---
title: 文件存储不足，特定页面加载缓慢
description: 针对大型、富映像带来的磁盘空间低的问题提供了解决方案。
exl-id: 640c8f0d-f714-4cc1-a401-9264cfaf8e37
feature: Storage, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# 文件存储不足，特定页面加载缓慢

针对大型、富映像带来的磁盘空间低的问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有受支持的版本
* Adobe Commerce内部部署，所有受支持的版本
* Magento Open Source，所有受支持的版本

## 问题

磁盘存储量低和页面加载速度慢可能是由大量富映像在`pub/media/catalog/products`中使用大量存储以及在暂存和生产环境之间共享磁盘空间造成的（除非配置了专用的暂存环境）。

## 原因

图像未经过优化以平衡性能和观看质量。

## 解决方案

在上传图像之前，请优化并压缩图像以平衡性能和观看质量。 这有助于增加空间并减少页面加载时间。 对于具有大面积纯色区域的图像，PNG提供了更小的大小。 JPEG会为其他内容提供更小的大小。 使用最高的压缩率（无明显降级）。 通常是60-80%。

使用[Fastly图像优化](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html)生成存储效率更高的图像。

## 相关阅读

要了解有关管理磁盘空间(如果您在云基础架构上的Adobe Commerce上)的信息，请参阅《云基础架构上的Adobe Commerce指南》中的[在Commerce中管理磁盘空间](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html)。
