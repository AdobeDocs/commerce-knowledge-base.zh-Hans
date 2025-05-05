---
title: Elasticsearch索引状态为“黄色”或“红色”
description: 本文修复了Elasticsearch索引状态不是“*green*”的问题。 “*yellow*”表示正常，“*red*”表示损坏。 “黄色”或“红色”状态可能会与缺少产品或显示旧产品信息同时出现。
exl-id: 27689511-6a41-41a9-8dda-a627d2f65263
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Elasticsearch索引状态为“黄色”或“红色”

>[!WARNING]
>
> 将在Adobe Commerce 2.4.0[&#128279;](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)中删除MySQL目录搜索引擎。 在安装版本2.4.0之前，必须设置并配置Elasticsearch主机。请参阅[安装和配置Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)。

文章修复了Elasticsearch索引状态不是“*绿色*”的问题。 “*黄色*”表示正常，“*红色*”表示错误。 “黄色”或“红色”状态可能会与缺少产品或显示旧产品信息同时出现。

## 受影响的版本和产品

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x

## 问题

Elasticsearch目录搜索索引缓慢，导致状态为“*黄色*”或“*红色*”，而不是“*绿色*”。 您还可能会遇到前端缺少更改的情况。

## 原因

可能有很多潜在的原因。 一个原因是Elasticsearch实例的磁盘空间不足。 另一个原因是重复的索引。

## 解决方案

在执行以下步骤之前创建新的mysql转储，并在工作时间之外执行这些转储以避免潜在影响您的客户端：

1. 临时切换到MySQL搜索 — 启用MySQL搜索。 (注意：请记得切换回Elasticsearch，否则您可能会遇到性能问题)。
1. 要识别重复的索引，请运行以下命令：

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

1. 要删除索引，请执行以下操作：

   ```
   curl -XDELETE localhost:9200/[your_index_name_here]
   ```

1. 重新启用Elasticsearch。
1. 运行完全重新索引。
1. 通过运行以下命令检查索引状态：

   ```
   curl --silent -X GET localhost:9200/_cat/indices?v
   ```

如果这些步骤不起作用，[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

## 相关阅读

若要了解详细信息，请参阅[Elasticsearch群集运行状况API](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)。
