---
title: 正在监视 [!DNL Adobe Commerce on cloud pro infrastructure]的情况说明书
description: 本文档提供有关Adobe Commerce基础架构监控和通知的信息。
exl-id: 01342d8d-2123-4455-b1a5-a08a5805b046
feature: Cloud
source-git-commit: 27fed162416c619a08d757279a3405f1fa72e976
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# 正在监视[!DNL Adobe Commerce on cloud pro infrastructure]的情况说明书

本文档提供有关Adobe Commerce基础架构监控和通知的信息。

通过监控，商家、系统集成商和Adobe的内部团队可以排查网站可用性和磁盘空间不足的问题。

## 问题疑难解答和解决

Adobe Commerce实例通常包含自定义代码和配置。 Adobe不支持或解决自定义代码和配置的问题。 Adobe确实帮助商家排除和识别我们知识库中的问题，并提供用于预防和解决这些问题的推荐解决方案和最佳实践。 我们鼓励商家和合作伙伴使用下表了解哪些内容受到监控以及谁负责解决问题。

触发通知时，Adobe Commerce支持团队将分类问题。 作为分类的一部分，将分析错误日志和其他资源。 根据分类，会为商家或合作伙伴（如果为自定义更新）或Adobe的内部团队创建其他[!DNL Zendesk]支持工单以解决该问题。

## Adobe Commerce：默认监控

将监控以下事件，Adobe Commerce团队会采取必要步骤来解决和传达发现的问题。

## 站点可用性监控

| 站点可用性 | 描述 |
|------------|------------|
| **监视目标** | 跟踪站点可用性。 |
| **检测日期** | 为高[!DNL SLA]选择单个[!DNL URL]。 |
| **描述** | 站点可用性是根据围绕度量配置的阈值确定的。 如果检查失败10分钟并且没有正在进行的活动部署，则会触发站点中断通知。 |
| **通知收件人** | 商家/合作伙伴和Adobe。 |
| 由Adobe执行的&#x200B;**操作** | 负责对Adobe Commerce基础架构是否存在问题进行分类和修复。 |
| **商家执行的操作** | 负责修复由商家/合作伙伴引入的更改或自定义代码导致的问题。 有关疑难解答，请参阅： [Site Down Troubleshooter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=zh-Hans)。 |

## Diskspace监控

| Diskspace监控 | 描述 |
|------------|------------|
| **监视目标** | 用于跟踪磁盘空间使用情况。 |
| **检测日期** | [!DNL MySQL]个磁盘和媒体磁盘分区。 |
| **指标** | 主机上每分钟都会监视可用磁盘空间。 如果仅留下5%或2 GB可用空间，则会引发警告。 在剩余可用空间处设置的临界阈值为2%或1 GB。 |
| **描述** | 根据针对主机的可用磁盘空间配置的阈值发送通知。 自动向相关装载（[!DNL MySQL]或介质）添加一次额外的磁盘空间，以防止站点中断，并给商家留出时间来清除磁盘空间和/或识别并解决导致磁盘使用率快速增加的任何代码或日志。 |
| **通知收件人** | 商家/合作伙伴和Adobe。 |
| 由Adobe执行的&#x200B;**操作** | 自动提高支持票证，并将额外的磁盘空间自动添加到相关装载（[!DNL MySQL]或媒体）以防止站点中断。 |
| **商家执行的操作** | 要接收持续的警告级别磁盘空间警报，请参阅： <ul><li>[[!DNL Managed alerts for Adobe Commerce]：磁盘警告警报](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert)</li><li>[[!DNL Managed alerts for Adobe Commerce]：磁盘严重警报](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert) </li></ul> |
