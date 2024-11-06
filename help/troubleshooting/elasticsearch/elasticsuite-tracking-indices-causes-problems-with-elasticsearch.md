---
title: ElasticSuite跟踪索引导致Elasticsearch出现问题
description: 本文讨论ElasticSuite插件生成的跟踪索引所导致的Elasticsearch内存问题。
exl-id: 67bfd06a-c801-4306-8510-a84a6fe5351a
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ElasticSuite跟踪索引导致Elasticsearch出现问题

>[!NOTE]
>
>ElasticSuite及其关联应用程序是Adobe目前不支持的第三方工具。 此内容仅作为信息性内容显示，不能作为支持范围启用内容的指示。

本文讨论ElasticSuite插件生成的跟踪索引所导致的Elasticsearch内存问题。

## 受影响的产品和版本

ElasticSuite 2.8.0之前的版本无法定期清理跟踪索引。

早于2.9.8 / 2.10.7的ElasticSuite版本在每日索引中存储跟踪索引，这会导致开放索引的数量增加。

## 问题

如果安装了ElasticSuite第三方插件，您可能会遇到Elasticsearch内存问题，并且Elasticsearch服务可能会因ElasticSuite跟踪索引而崩溃。 症状包括：

* Elasticsearch崩溃，无内存错误。
* 运行运行状况命令`curl -m1 localhost:9200/_cluster/health?pretty`或`curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`（对于入门帐户）时，`unassigned_shards`有数百或数千个
* Elasticsearch或站点性能严重降低。
* 在Elasticsearch部署或日志错误中，*“在您的群集中未找到活动节点”*。
* *在部署或日志错误中拒绝到[&lt;\*>_ tracking_log_event _&lt;\*>]“*”的映射更新。

## 原因

ElasticSuite具有创建跟踪索引的新功能。 这些跟踪索引记录哪些搜索词使用最多、哪些词产生最多成交额，以及哪些词导致无结果页面，以便商家可以创建同义词来修复它们。 它似乎不会删除跟踪索引，因此Elasticsearch会耗尽资源并崩溃。

## 解决方案

### 请升级您的ElasticSuite版本，以便能够定期清理跟踪索引

将ElasticSuite插件升级到高于2.8.0的版本后，即可配置索引的定期清理。

转到&#x200B;**商店** > **配置** > **跟踪** > **全局配置** > **保留延迟**

默认保留期为365天。 您可以将其缩短到30或15天。

### 升级您的ElasticSuite版本，以使用基于月份的索引，而不是基于每日的索引

将ElasticSuite插件升级到2.9.8 / 2.10.7以上的版本后，将按月跟踪索引。

您仍然可以缩短保留期：

转到&#x200B;**商店** > **配置** > **跟踪** > **全局配置** > **保留延迟**

默认保留期为12个月（将生成12个索引）。 您可以将其缩短到3或6个月。

### 使用cronjob清理跟踪索引数据

创建cron作业以删除跟踪索引。 此命令删除在上个月创建的索引：

```
   curl -XDELETE localhost:9200/<name in index> * **\_tracking\_log** * _$(date
    +'%Y%m' -d 'last month')*
```

如果要在设定的时间频率删除索引，请通过引用开发人员文档中的以下文章来创建cron作业：

* [配置自定义cron作业和cron组（教程）](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/crons/custom-cron-tutorial)
* [设置cron作业](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property)
