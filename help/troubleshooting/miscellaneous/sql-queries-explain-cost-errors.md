---
title: 'SQL查询：说明成本错误'
description: 本文提供了在运行不成功的SQL查询时出现EXPLAIN开销错误的解决方案。 PostgreSQL使用名为[EXPLAIN命令](https://www.postgresql.org/docs/9.5/static/using-explain.html)的函数来确定SQL查询的开销。 我们构建的SQLReport Builder也使用此命令，这意味着如果认为成本过高（执行查询所需的资源量超过我们的阈值），查询将不会运行，并且会显示一条EXPLAIN消息。
exl-id: 6f6df66a-665e-46a8-ad4c-842a0270c4eb
feature: Commerce Intelligence
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# SQL查询： EXPLAIN成本错误

本文提供了在运行不成功的SQL查询时出现EXPLAIN开销错误的解决方案。 PostgreSQL使用名为[EXPLAIN命令](https://www.postgresql.org/docs/9.5/static/using-explain.html)的内容来确定SQL查询的成本。 我们构建的SQLReport Builder也使用此命令，这意味着如果认为成本过高（执行查询所需的资源量超过我们的阈值），查询将不会运行，并且会显示一条EXPLAIN消息。

发生这种情况的原因有几个。 以下是您可能会收到的消息、这些消息的含义以及如何排除这些消息。

## 无法执行查询。 \[xxx\]的EXPLAIN成本值太高，无法运行此查询。

如果您看到此消息，则表示该查询被视为太昂贵而无法执行。 针对这种情况，我们提出了两个建议：一个是从查询中删除任何ORDER BY子句，因为这些子句的操作成本很高。 第二个是按照我们的[优化文章](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/best-practices/data/optimizing-your-sql-queries.html)中的提示调整您的查询。

## 无法执行查询。 此查询返回\[xxx\]行，这超过了我们10,000行的限制

在这种情况下，可能的结果数超过了SQLReport Builder设置的最大值。 有几种方法可以减少结果数量：

* 尝试将一些筛选器添加到查询。
* 如果可以，请使用LIMIT 。 某些表的行数很大，如果限制结果，则可保持不超过行数限制。

## 无法解析EXPLAIN响应。

糟糕。 此消息通常意味着我们这边出现了问题。 如果您仍收到此错误，请联系支持人员。
