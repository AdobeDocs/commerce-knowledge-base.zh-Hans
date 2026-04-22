---
title: 电子邮件表明导出存储几乎已满
description: 本文针对您收到一封电子邮件，指出导出存储已几乎满的问题提供了解决方案。
feature: Cloud, Storage, Media
role: Developer
exl-id: 7dae295c-919c-46c5-bf63-7d3467c2e07f
source-git-commit: 11cf981c7ebe813219a0cd311632eafce086bbf6
workflow-type: tm+mt
source-wordcount: '427'
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

此警报是指导出存储文件系统，即存储介质和其他文件数据的磁盘卷。 此文件系统通常装载在`/data/exports`。 该警报不表示存在名为导出的单个目录。

要确认警报所指的是什么，请检查exports storage usage ：

* 运行`df -h | grep exports`，将显示以下示例输出：

  ```
  /dev/nvme1n1 50G 38G 12G 77% /data/exports
  tmpfs         7.7G 4.0K 7.7G  1% /data/exports/shared
  ```

* 在此示例中，`/data/exports`是主导出文件系统：

   * 总计50 GB
   * 38 GB已使用
   * 12 GB可用（77%利用率）

* `/data/exports/shared`是用于共享数据的`tmpfs` （内存中）装载，对磁盘压力没有显着影响。

这可以确认警报是由`/data/exports`的整体磁盘利用率触发的，而不是由名为exports的单个文件夹触发的。

如果`/data/exports`显示高利用率，则此文件系统下的大型目录（如pub/media或其他自定义文件位置）通常会导致使用率的增加。

## 解决方案

按照以下步骤查看、清理和验证exports存储的使用情况。

1. 运行命令`df -h | grep exports`以检查导出存储文件系统的当前使用情况。 查看&#x200B;**的**&#x200B;使用%`/data/exports`列：

   * 如果使用率为70-85%，则开始计划清理。
   * 如果使用率大于90%，请立即采取措施以避免写入失败或影响服务。

1. 通过运行以下命令，识别`/data/exports`下占用大量磁盘空间的目录：

   ```bash
   du -sh /data/exports/* 2>/dev/null
   ```

   文件存储可能填充的典型位置是`pub/media/catalog/product/cache`或`var/log`文件夹。

1. 根据环境清理文件：

   * 首先删除旧的或未使用的导出文件、日志或临时数据。
   * 在非生产环境中，您通常可以更积极地删除测试介质或旧工件。
   * 在生产环境中，在删除任何媒体或业务关键型文件之前，请与您的团队协调。

1. 清理后，运行以下命令`df -h | grep exports`以确认&#x200B;**的** Use%`/data/exports`值已降至安全操作级别。

## 相关阅读

[检查我们的支持知识库中的专用群集](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#check-dedicated-clusters)。
