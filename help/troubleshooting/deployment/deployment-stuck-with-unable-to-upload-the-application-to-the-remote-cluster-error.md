---
title: 部署卡住，出现“无法将应用程序上传到远程群集”错误
description: '本文为Adobe Commerce问题提供了一个解决方案，该问题导致部署卡住，并且在部署日志中可以找到以下错误消息：*"错误：无法将应用程序上传到远程群集"*。'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# 部署卡住，出现“无法将应用程序上传到远程群集”错误

本文为Adobe Commerce问题提供了一个解决方案，该问题导致部署卡住，并且可以在部署日志中找到以下错误消息： *&quot;错误：无法将应用程序上载到远程群集&quot;*。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

<u>重现步骤</u>：

手动触发部署，或通过执行环境的合并、推送或同步来触发部署。

<u>预期的结果</u>：

已成功完成部署。

<u>实际结果</u>：

部署卡住，在云UI的部署错误日志中，显示以下错误消息： *“错误：部署失败后无法将应用程序上传到远程群集”，站点可能会显示错误“503第一字节超时”*。

## 原因

问题是由可用存储的中断造成的。

## 解决方案

您可以考虑清除日志目录和/或增加磁盘空间。

考虑进行清理的目录：

* `var/log`
* `var/report`
* `var/debug/`
* `var`

有关如何在云基础架构的Adobe Commerce上增加磁盘空间入门计划体系结构的详细信息，请参阅我们的支持知识库中的[增加云上集成环境的磁盘空间](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md)。 相同的说明可用于在云基础架构上增加Adobe Commerce的空间专业规划架构集成环境。 对于Pro Production/Staging，您需要[向Adobe Commerce支持部门提交票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket)并请求增加磁盘空间。 但通常情况下，您无需在Pro计划的暂存/生产阶段处理此事宜，因为Adobe Commerce会为您监控这些参数，并根据合同发出警报和/或采取相应措施。
