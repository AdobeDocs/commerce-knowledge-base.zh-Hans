---
title: Adobe Commerce [!DNL Site-Wide Analysis Tool] 报告常见问题解答
description: 了解 [!DNL Site-Wide Analysis Tool]，这是一个主动式自助服务工具和中央存储库，其中包含详细的系统分析和建议，以确保Adobe Commerce安装的安全性和可操作性。
exl-id: 7c843d55-9e2c-4b18-8859-0ebad0ae28cf
feature: Best Practices, Saas, Support, Tools and External Services
role: Admin
source-git-commit: 580ad148cd4346868cd9892a1ae9a4d85f73edce
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Adobe Commerce [!DNL Site-Wide Analysis Tool]报告常见问题解答

>[!IMPORTANT]
>
>自2024年4月23日起，所有Adobe Commerce本地客户都将停用[!DNL Site-Wide Analysis Tool]。

本文介绍了每月或每季度为Adobe Commerce on cloud infrastructure客户自动生成的[!DNL Site-Wide Analysis Tool]报表。

>[!NOTE]
>
>在Adobe Commerce on cloud infrastructure v2.4.1及更高版本中，[!DNL Site-Wide Analysis Tool]可通过Commerce管理面板使用。 因此，客户可以直接运行[!DNL Site-Wide Analysis Tool]报告。 有关访问详细信息，请参阅[[!DNL Site-Wide Analysis Tool] 指南](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/access.html)。

## 什么是[!DNL Site-Wide Analysis Tool]？

[!DNL Site-Wide Analysis Tool]是一个SaaS应用程序，它执行端到端“时间点”客户站点分析（在[!DNL Site-Wide Analysis Tool]环境中，而不是在客户站点上）。 所有与[!DNL Site-Wide Analysis Tool]相关的客户站点信息都是按预定计划收集的，时间范围从每3小时到每天一次。 这意味着[!DNL Site-Wide Analysis Tool]正在不断分析客户站点数据以获得调查结果。

## 什么是[!DNL Site-Wide Analysis Tool]报告？

[!DNL Site-Wide Analysis Tool]报告是自助服务、最佳实践推荐的调查结果（问题）列表，可通过Adobe Commerce支持票证系统以PDF形式发送给客户。

## [!DNL Site-Wide Analysis Tool]报表中包含哪些信息？

[!DNL Site-Wide Analysis Tool]报表中提供的站点信息包括：

* 调查结果
   * 概述，包括实施修复顺序的“优先级”
   * 查找结果描述
   * 前提条件（如果有）
   * 网站影响
   * 根本原因
   * 推荐
* 异常日志
   * 记录异常信息
   * 上次发生的日期
   * 异常发生的次数

## 谁会收到每月自动发送的[!DNL Site-Wide Analysis Tool]报表？

目前，那些运行状况指数低（等于或低于当前设置的性能阈值）的客户将通过支持票证系统每月收到其生产环境的[!DNL Site-Wide Analysis Tool]报告。[!DNL Site-Wide Analysis Tool]

## 谁会收到自动提供的[!DNL Site-Wide Analysis Tool]季度报告？

所有客户（不论[!DNL Site-Wide Analysis Tool]运行状况指数如何）都将通过支持票证系统收到其生产环境的季度[!DNL Site-Wide Analysis Tool]报告。

## 如何传送报表？

每月或每季度通过Adobe Commerce支持票证系统自动交付[!DNL Site-Wide Analysis Tool]报告。 还可以从[!DNL Site-Wide Analysis Tool]仪表板手动生成[!DNL Site-Wide Analysis Tool]报告并将其保存到桌面。 然后，可以将这些[!DNL Site-Wide Analysis Tool]报告作为附件通过电子邮件发送。

>[!NOTE]
>
>应用推荐后，手动生成报告不会更新推荐 — 从[!DNL Site-Wide Analysis Tool Dashboard]中删除它可能需要几天时间。
