---
title: 磁盘空间不足
description: 本文针对云基础架构上的Adobe Commerce的特定环境中空间不足的情况提出了解决方案。
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# 磁盘空间不足

本文针对云基础架构上的Adobe Commerce的特定环境中空间不足的情况提出了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

具有可写目录的磁盘上的磁盘空间不足。 一个症状可能是[停滞的部署](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26878)。

要检查磁盘使用情况，请运行以下命令：

```bash
df -h var/
```

## 原因

`var`目录通常占用大量空间，可以轻松清理。

Adobe Commerce将所有日志文件存储在`var`目录中。 将创建新的日志文件，每天存档旧日志文件。 但是，如果生成的错误数量不断增长，则日志文件将占用越来越多的空间。

自定义导入/导出文件也存储在`var`目录中，如果文件数量增加，则占用空间。

## 解决方案

解决方案选项：

* 检查是否有大型日志文件，并调查其大型的原因，修复生成大量日志输出的问题。
* 清理`var`目录。
* 设置cron作业以跟踪`var`目录的大小并清理它。
* 分配更多磁盘空间（如果您有未使用的空间）。 （有关如何检查您的空间限制的信息，请参阅以下部分。）
   * 对于入门计划、所有环境和Pro计划集成环境，如果您有一些未使用的磁盘空间，则可以分配磁盘空间，如[管理磁盘空间：分配磁盘空间](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space)中所述。
   * 对于Pro Plan暂存和生产环境，如果您有一些未使用的磁盘空间，请联系支持人员以分配更多磁盘空间。
* 如果您已达到空间限制但仍遇到空间不足问题，请考虑购买更多磁盘空间，请联系您的Adobe客户团队以了解详细信息。

### 检查磁盘空间限制

要检查在云基础架构环境中每个Adobe Commerce有多少空间，请执行以下操作：

1. 登录到[云控制台](https://console.adobecommerce.com)。
1. 在&#x200B;**[!UICONTROL All projects]**&#x200B;仪表板上，选择相关项目。 在左角，您可以看到磁盘空间可用性。

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
