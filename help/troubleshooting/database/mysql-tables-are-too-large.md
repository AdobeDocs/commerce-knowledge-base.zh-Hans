---
title: MySQL表太大
description: 本文讨论了当任何MySQL表大于1 GB时为什么会出现问题以及如何防止出现此问题。
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# MySQL表太大

本文讨论了当任何MySQL表大于1 GB时为什么会出现问题以及如何防止出现此问题。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.x.x
* Adobe Commerce内部部署2.x.x

## 问题

MySQL表的大小不会直接影响站点性能。 但是，如果表很大，则意味着此表频繁执行插入操作，可能会有额外数据或过期数据。 MySQL是针对读/写操作比例为80%/20%的数据库而设计的。  对于大表（1 GB及更大容量），MySQL索引旨在提高读取操作的性能，但可能会降低写入操作的性能。

## 解决方案

请考虑以下选项以避免性能降低：

* 创建CRON作业，这将清理大表。 请参阅 [查找大型MySQL表](/help/how-to/general/find-large-mysql-tables.md) 在我们的支持知识库中获取有关如何标识大表的建议。
* 对于大于1 GB的表，请使用为日志写入优化的MySQL引擎。 例如，Archive引擎。
* 更新功能以避免将日志存储在数据库中。

## 相关阅读

[更改日志表过大，导致实体更新延迟](/help/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront.md) 在我们的支持知识库中。
