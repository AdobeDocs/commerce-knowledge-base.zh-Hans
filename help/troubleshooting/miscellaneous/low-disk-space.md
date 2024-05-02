---
title: 磁盘空间不足
description: 本文针对云基础架构上的Adobe Commerce的特定环境中空间不足的情况提出了解决方案。
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 磁盘空间不足

本文针对云基础架构上的Adobe Commerce的特定环境中空间不足的情况提出了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

具有可写目录的磁盘上的磁盘空间不足。 一个症状可能是 [停滞部署](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

要检查磁盘使用情况，请运行以下命令：

```bash
df -h var/
```

## 原因

此 `var` 目录通常是占用大量空间且易于清理的目录。

Adobe Commerce将所有日志文件存储在 `var` 目录。 将创建新的日志文件，每天存档旧日志文件。 但是，如果生成的错误数量不断增长，则日志文件将占用越来越多的空间。

自定义导入/导出文件也存储在 `var` 目录，如果它们的数量增加，请留出空间。

## 解决方案

解决方案选项：

* 检查是否有大型日志文件，并调查其大型的原因，修复生成大量日志输出的问题。
* 清理 `var` 目录。
* 设置cron作业以跟踪 `var` 目录并进行清理。
* 分配更多磁盘空间（如果您有未使用的空间）。 （有关如何检查您的空间限制的信息，请参阅以下部分。）
   * 对于入门计划、所有环境和专业计划集成环境，如果您有一些未使用的磁盘空间，则可以分配磁盘空间，如中所述 [管理磁盘空间：分配磁盘空间](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * 对于Pro Plan暂存和生产环境，如果您有一些未使用的磁盘空间，请联系支持人员以分配更多磁盘空间。
* 如果您已达到空间限制但仍遇到空间不足问题，请考虑购买更多磁盘空间，请联系您的Adobe客户团队以了解详细信息。

### 检查磁盘空间限制

要检查在云基础架构环境中每个Adobe Commerce有多少空间，请执行以下操作：

1. 登录到 [云控制台](https://console.adobecommerce.com).
1. 在 **[!UICONTROL All projects]** 仪表板中，选择相关的项目。 在左角，您可以看到磁盘空间可用性。

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
