---
title: 电子邮件表明导出存储几乎已满
description: 本文针对您收到一封电子邮件，指出导出存储已几乎满的问题提供了解决方案。
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 89f985b832545f1fbccf94aac1d60f1e767b5bc4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 电子邮件表明导出存储空间几乎已满

本文针对您收到一封电子邮件，指出导出存储已几乎满的问题提供了解决方案。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 问题

您收到一封包含以下内容的电子邮件，但无法找到&#x200B;*exports*&#x200B;文件夹：

*我们的监控检测到您的群集XXX上的“exports”存储已满大约“85%”。*
*如果需要，请检查用法、进行清理或请求升级。*
*另外，请注意，当存储达到临界阈值级别时，我们将自动尝试进行升级。*

## 原因

电子邮件指的是&#x200B;**exports**&#x200B;存储空间，这是分配给文件/媒体的磁盘数量，而不是名为&#x200B;*exports*&#x200B;的特定文件夹。

## 解决方案

您应该查看环境中的文件使用情况。 运行此命令以获取现有用法：

`df -h |grep data`

文件存储可能填充的典型位置为&#x200B;*pub/media/catalog/product/cache*&#x200B;或&#x200B;*var/log*&#x200B;文件夹。 要确定文件使用的磁盘空间，请使用适当的路径&#x200B;*/path/to/folder*&#x200B;运行此命令：

`du -shc` */path/to/folder*

如果介质磁盘的使用量占总磁盘空间的大部分，则可能需要考虑启用[Fastly深度映像优化](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization#deep-image-optimization)，然后手动删除服务器上&#x200B;*pub/media/catalog/product/cache*&#x200B;文件夹中的文件。

## 相关阅读

[检查我们的支持知识库中的专用群集](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters)。
