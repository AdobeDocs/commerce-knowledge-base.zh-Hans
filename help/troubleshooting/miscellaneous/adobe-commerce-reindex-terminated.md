---
title: “Adobe Commerce cloud：使用‘已终止’消息终止重新索引”
description: '* Adobe Commerce on cloud infrastructure（所有版本）'
exl-id: 36ed9c9f-8280-41db-9df3-fe842dade4b1
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Adobe Commerce cloud：重新索引终止 `Killed` message

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本）

## 问题

您正尝试在集成分支（或在入门体系结构项目的暂存阶段）上运行重新索引，此过程将终止 `Killed` 消息。

## 原因

发生这种情况通常是由于PHP进程内存不足。
最常见的原因是实例上存在大量产品、商店和/或客户组。

## 解决方案

1. 减少产品数量（以及客户组和商店 — 如果适用）。
1. 仅限一个或两个并发用户使用。
1. 禁用cron作业，并根据需要手动运行。
1. 如果之前未执行此操作，请请求升级到增强集成环境 — 请注意，一旦执行升级，您将受到环境数量限制。 请参阅 [集成环境增强请求 — Pro和Starter](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) 请参阅我们的支持知识库中的文章，以了解详细信息。

## 相关阅读：

在我们的开发人员文档中：

* [专业体系结构>集成环境](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#cloud-arch-int)
* [入门体系结构>暂存环境](https://devdocs.magento.com/cloud/architecture/starter-architecture.html#cloud-arch-stage)
