---
title: Adobe Commerce [!DNL crons] 已禁用，无需干预
description: 使用本文可修复在没有干预的情况下禁用 [!DNL crons] 的问题。
exl-id: 5172d2ae-53ad-4db6-ae00-7b27c96911e9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Adobe Commerce crons已禁用，无需干预

本文为无干预禁用[!DNL crons]提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## 问题

您的[!DNL crons]在部署后已禁用。

<u>重现步骤</u>：

部署。

<u>预期的结果</u>：

您的[!DNL crons]正在运行。

<u>实际结果</u>：

您的[!DNL crons]在部署后已禁用。

## 原因

[!DNL OPcache]设置有问题。

## 解决方案

将[!DNL ECE Tools]升级到最新版本[2002.1.13](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package#v2002113)。

## 相关阅读

* [我们的支持知识库中性能缓慢、运行缓慢且时间较长 [!DNL crons]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.html)。
* [[!DNL Cron] 任务锁定我们支持知识库中其他组](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.html?lang=en)的任务。
* [[!DNL Cron] 作业卡在我们的支持知识库中，处于“正在运行”状态](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en)。
