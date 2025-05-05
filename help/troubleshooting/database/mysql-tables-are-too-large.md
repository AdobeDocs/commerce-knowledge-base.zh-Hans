---
title: “[!DNL MySQL]表太大”
description: 本文讨论当任何 [!DNL MySQL] 表大于1 GB时为什么会出现问题以及如何防止出现此问题。
exl-id: 43f74e3b-7f2e-428c-9964-56d2ce98a34d
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# [!DNL MySQL]表太大

本文讨论当任何[!DNL MySQL]表大于1 GB时为什么会出现问题以及如何防止出现此问题。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.x.x
* Adobe Commerce内部部署2.x.x

## 问题

[!DNL MySQL]表大小不会直接影响站点性能。 但是，如果表很大，则意味着此表频繁执行插入操作，可能会有额外数据或过期数据。 [!DNL MySQL]是为数据库设计的，其中读/写操作之间的比率为80%/20%。  对于大型表，1 GB及更高的[!DNL MySQL]索引旨在提高读取操作的性能，但可能会降低写入操作的性能。

## 解决方案

请考虑以下选项以避免性能降低：

* 创建CRON作业，这将清理大表。 请参阅我们的支持知识库中的[查找大型 [!DNL MySQL] 表](/help/how-to/general/find-large-mysql-tables.md)，以获取有关如何识别大型表的建议。
* 对于大于1 GB的表，请使用为日志写入优化的[!DNL MySQL]引擎。 例如，Archive引擎。
* 更新功能以避免将日志存储在数据库中。

## 相关阅读

* [超大的更改日志表导致我们的支持知识库中的实体更新延迟](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/database/changes-in-the-database-are-not-reflected-on-the-storefront)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
