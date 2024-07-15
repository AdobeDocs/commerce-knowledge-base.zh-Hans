---
title: 云基础架构上的Adobe Commerce中的磁盘空间不足时安全删除文件
description: 本文为磁盘空间不足并需要安全删除文件的情况提供了解决方案。 在考虑此操作之前，请查看我们的开发人员文档中的[管理磁盘空间](https://devdocs.magento.com/cloud/project/manage-disk-space.html#no-space-left)。 如果该文章中的步骤不适合您或者不能解决问题，请查看本文中的步骤。
exl-id: 6b0a5c1a-8db4-49d7-a785-b4e0bbaea0df
feature: Cloud, Paas
role: Developer
source-git-commit: 86515936f72bbd0a5778cb81f665993ed91e4707
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 云基础架构上的Adobe Commerce中的磁盘空间不足时安全删除文件

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.2 - 2.4.7
* 这特定于专用的Pro群集。 起始环境和集成环境是单个节点，没有`/data/exports`目录。

## 磁盘空间不足的迹象

磁盘空间不足的迹象可能是部署停滞、磁盘满载警告和性能不佳。
要查看文件系统使用的磁盘空间量，请在CLI/终端中运行以下命令：

`df -h`


## 如何安全地删除文件以增加磁盘空间

您可以从应用程序的装入点、您的`/app`路径或通过`/mnt/shared`删除文件。 访问相同文件有两种不同的方式。

>[!WARNING]
>
>**从不修改或删除`/data/exports`**&#x200B;的内容。
>
>`/data/exports`是共享文件系统的基础存储，由GlusterFS管理。
>
>该处的文件系统不仅包含文件内容，还包含有关文件系统状态的元数据，以允许群集节点之间的同步。 **直接在此文件系统内更改或删除文件将损坏共享>文件系统，需要进行大量修复或数据恢复。**

要查找可能适合清除的最大文件，请运行以下命令（在大型或繁忙的项目中，最多可能需要一小时）：

```bash
FS='/data/exports';NUMRESULTS=20;resize;clear; echo "Please find below the Largest Directories and Files:";date;df -h $FS; echo "Largest Directories:";nice -n 19 find /app/*/ -type d -ls 2>/dev/null| sort -rnk1| head -n $NUMRESULTS| awk '
{printf "%d MB %s\n", $1/1024,$2}
';echo "Largest Files:"; nice -n 19 find /app/*/ -type f -ls 2>/dev/null| sort -rnk7| head -n $NUMRESULTS|awk '
{printf "%d MB\t%s\n", ($7/1024)/1024,$NF}
'; echo "Please use the above information to clear any unwanted data from the server, it is important this is done as soon as possible to ensure your server stays functional.";
```

该命令的输出将包含指定大小的最大文件和目录的列表。

## 相关阅读

在我们的支持知识库中：

* [增加云上集成环境的磁盘空间](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)
* [磁盘空间不足](/help/troubleshooting/miscellaneous/low-disk-space.md)

在我们的开发人员文档中：

* [管理磁盘空间](https://devdocs.magento.com/cloud/project/manage-disk-space.html)
