---
title: 检查日志以对Adobe Commerce上的500和503错误进行故障排除
description: 本文介绍如何检查“access.log”和相关日志，以排查503和500错误（这些错误可能由流量或服务器资源不足引起）。 查看“access.log”和相关日志可以提供有关云基础架构上Adobe Commerce相关问题的可能原因的信息。
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# 检查日志以对Adobe Commerce上的500和503错误进行故障排除

本文说明如何检查 `access.log` 和相关日志，用于排查503和500错误，这些错误可能由流量或服务器资源不足引起。 查看 `access.log` 和相关日志可以提供有关哪些因素可能导致与云基础架构上的Adobe Commerce有关的问题的信息。

<!--
Bob - not in TOC
-->

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，全部 [支持的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html).

要查看这些服务器错误的日志，请检查 `access.log` 在Web服务器上，例如 `<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

要检查相关日志，请执行以下操作：

1. 如果是在当天，请在CLI中运行以下命令(适用于云基础架构上的Adobe Commerce Pro计划架构)。 或者直到过去的某个时间点(对于云基础架构入门计划架构上的Adobe Commerce)，因为日志的覆盖范围持续时间有限，并且日志轮换不可用： `grep -r "\" [50[0-9]" /path/to/access.log` 如果以前发生错误，请在CLI中运行以下命令（仅限Pro体系结构）： `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. 然后查看 `exception.log` 和 `error.log` 或等效项 [轮换的日志](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#log-rotation) （达到特定文件大小时自动旋转和压缩的日志）来查找潜在错误，并查看可能已发生的情况以找到导致该错误的原因。 注：要检查 `exception.log` 和 `error.log` 在CLI中运行上述命令但替换 `access.log` 替换为 `exception.log` 或 `error.log`.

## 相关阅读

* 请参阅 [查看和管理日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) 在 *《云基础架构上的Adobe Commerce指南》*.
* 请参阅 [503错误故障诊断](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md) 在我们的支持知识库中。
* 请参阅 [Magento站点停止疑难解答程序](/help/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.md) 在我们的支持知识库中。
