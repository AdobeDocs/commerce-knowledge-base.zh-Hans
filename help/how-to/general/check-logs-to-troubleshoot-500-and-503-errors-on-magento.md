---
title: 检查日志以对Adobe Commerce上的500和503错误进行故障排除
description: 本文介绍如何检查“access.log”和相关日志，以排查503和500错误（这些错误可能由流量或服务器资源不足引起）。 查看“access.log”和相关日志可以提供有关云基础架构上Adobe Commerce相关问题的可能原因的信息。
exl-id: 47d7de6b-3e12-4e79-a5c1-c27a9196b99c
feature: Cloud, Logs
source-git-commit: 66ac9de94e9a4a1eccdb5aac1875ecf0a0637e90
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 检查日志以对Adobe Commerce上的500和503错误进行故障排除

本文介绍如何检查`access.log`和相关日志以排查503和500错误（可能由流量或服务器资源不足引起）。 查看`access.log`和相关日志可以提供有关云基础架构上Adobe Commerce相关问题可能由哪些原因导致的信息。

<!--
Bob - not in TOC
-->

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=zh-Hans)。

要查看这些服务器错误的日志，请检查Web服务器上的`access.log`，例如`<ip address>` `<timestamp>` `<request uri>` `<response code>` `<referer url>`

要检查相关日志，请执行以下操作：

1. 如果是在当天，请在CLI中运行以下命令(适用于云基础架构上的Adobe Commerce Pro计划架构)。 或者过去某个时间点(适用于云基础架构上的Adobe Commerce入门计划架构)，因为日志的覆盖范围持续时间有限，并且日志轮换不可用： `grep -r "\" [50[0-9]" /path/to/access.log`如果过去发生错误，请在CLI中运行以下命令（仅限Pro架构）： `zgrep "\" 50[0-9]" /path/to/access.log.<rotation ID>.gz`
1. 然后，检查`exception.log`和`error.log`或等效的[轮换的日志](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html?lang=zh-Hans#log-rotation)（达到特定文件大小时自动轮换和压缩的日志）以了解相同的时间戳，以找到潜在的错误，并查看可能已发生什么导致该错误。 注意：若要检查`exception.log`和`error.log`，请在CLI中运行上述命令，但将`access.log`替换为`exception.log`或`error.log`。

## 相关阅读

* 请参阅[云基础架构上的Adobe Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hans)中的&#x200B;*查看和管理日志*。
* 请参阅我们的支持知识库中的[503错误疑难解答](/help/troubleshooting/miscellaneous/troubleshooting-503-errors.md)。