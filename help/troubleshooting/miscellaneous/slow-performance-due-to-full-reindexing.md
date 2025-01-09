---
title: 由于完全重新索引，性能缓慢
description: 本文修复了由于完全重新索引（其中与索引相关的数据库表中的数据正在更新）而导致性能不佳的问题。
exl-id: 4f20a862-cf54-4196-8a88-101f0c80f8f1
feature: Best Practices
role: Developer
source-git-commit: 72ee49a8667f575a58e0cf1b3d5c9df936cc628b
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# 由于完全重新索引，性能缓慢

本文修复了由于完全重新索引（其中与索引相关的数据库表中的数据正在更新）而导致性能不佳的问题。

## 受影响的版本和产品

* 云基础架构上的Adobe Commerce 2.x.x
* Adobe Commerce内部部署2.x.x

### 问题

不断刷新和索引重建是性能下降的部分原因。 此外，持续的完整重新索引会添加对表的锁定，使网站的工作速度远远低于预期。

### 原因

从管理员处执行了可生成完整重新索引的操作，包括：

* 产品属性保存
* 网站/商店/商店视图保存
* 存储配置

>[!NOTE]
>
>这些操作应在营业时间以外运行，以确保这些操作不会影响营业时间的性能。

[第三方扩展](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento)也可能导致完全重新索引。 也可以从CLI手动运行完全重新索引。 要了解是否重新索引了索引并可能导致性能降级，请执行以下操作：

1. 执行此查询可查找在过去15分钟内完全重新编制索引的索引器：

   ```
   SELECT * FROM indexer_state WHERE updated > NOW() - INTERVAL 15 MINUTE;
   ```

   输出中的索引器名称表示在过去15分钟内，索引器至少被重新索引过一次。

1. 如果发现频繁的完全重新索引，请检查以下各项：
   * 谁可能从CLI手动执行此操作
   * 第三方模块正在执行何种重新索引
   * 哪个第三方模块将索引器标记为&#x200B;*无效*

### 解决方案

仅在必要时运行重新索引。 有关步骤，请查看我们的开发人员文档中的[配置索引器](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers)。 一般建议和最佳做法是允许部分索引机制处理数据索引，而无需商家采取手动行动。 应使用本机Adobe Commerce功能(Mview)完成所有索引调整。 Mview执行部分重新索引，这是重新索引数据的最有效方法。 要了解Mview，请参阅我们的开发人员文档中的[索引概述： Mview](https://developer.adobe.com/commerce/php/development/components/indexing/#mview)。

## 相关阅读

* [索引概述：如何在我们的开发人员文档中重新索引](https://developer.adobe.com/commerce/php/development/components/indexing/#how-to-reindex)。
* [无效缓存导致支持知识库中的响应时间降低](/help/troubleshooting/miscellaneous/invalidated-cache-causes-response-time-degradation.md)。

