---
title: 诊断数据差异
description: 本文提供了解决Magento Business Intelligence(MBI)报表与查询或第三方报表之间差异问题的解决方案。
exl-id: 7d1156cb-9e9b-4426-a0ca-8890b815c245
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 诊断数据差异

本文提供了解决Magento Business Intelligence(MBI)报表与查询或第三方报表之间差异问题的解决方案。

根据分析的复杂性，生成相应的MBI报告可能需要熟悉平台的许多不同方面。 此清单和相关链接将帮助您了解报告背后的逻辑，使您能够识别任何差异的来源。

1. 如果团队中的其他成员创建了报告，则从确认其分析的目标和参数开始。
1. 根据查询、第三方报表工具或公式生成要与MBI报表进行比较的预期数据点。
1. 通过Report Builder中的指标链接或通过访问[系统摘要](https://support.magento.com/hc/en-us/articles/360016730971-Understand-View-definitions-of-metrics-filters-columns-and-column-references-in-the-System-Summary)选项卡来查看和确认[指标](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-metrics.html)定义：
   * 数据表
   * 操作
   * 操作数列，包括其计算方式（如果导出）（通过“系统摘要”）
   * 时间戳
   * 对于订阅量度：开始日期和结束日期
   * 已应用的筛选器，包括任何[筛选器集](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/build/reports/ess-manage-data-filters.html)中包含的筛选器
1. 查看并确认报表中的其他数据操作：
   * 公式已计算
   * [分组](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html#groupby)
   * [透视](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * [时间选项](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/tutorials/using-visual-report-builder.html)
   * 对于[同类群组分析](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis)：同类群组日期
   * 对于[同类群组分析](https://support.magento.com/hc/en-us/articles/360016504632-Create-cohort-analysis)：同类群组透视
1. 如果差异涉及最近的数据，请查阅“连接”页面上的&#x200B;**更新详细信息**&#x200B;部分以确认最新的可用数据点。
1. 如果分析中使用的量度是在数据库中某个表上生成的，而该表中曾删除过某些行，请与MBI支持团队确认是否正在检查该表中已删除的行，以及重新检查该表的频率和[复制方法](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/opt-db-analysis.html)。
1. 同样，如果在添加行后可以修改分析中使用的列，请向支持人员确认正在[检查这些列的修改](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/warehouse-manager/cfg-data-rechecks.html)以及重新检查的频率。

**仍为空白？**&#x200B;不必担心 — 我们随时为您提供帮助。 使用[这些说明](/help/troubleshooting/miscellaneous/mbi-data-discrepancies.md)向我们发送请求。
