---
title: Adobe Commerce疑难解答中的Elasticsearch
description: 使用Elasticsearch疑难解答工具可解决Adobe Commerce上的Elasticsearch问题。 单击每个问题以显示故障诊断程序每个步骤的答案。
exl-id: acae0da0-2918-4021-9fbe-c138940c5a72
feature: Categories
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 0%

---

# Adobe Commerce疑难解答中的Elasticsearch

使用Elasticsearch疑难解答工具可解决Adobe Commerce上的Elasticsearch问题。 单击每个问题以显示故障诊断程序每个步骤的答案。

>[!WARNING]
>
>关于Adobe Commerce on cloud infrastructure，请注意，如果没有48个工作小时的通知，就无法将服务升级推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产前48小时[提交支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，其中详细列出所需的服务升级并指明希望升级过程开始的时间。

## 步骤1 — 检查Elasticsearch问题 {#step-1}

+++**您的问题是否与Elasticsearch有关？**

错误消息指示的Elasticsearch问题、“_在群集中未找到活动节点”、_&#x200B;缺少产品以及旧产品信息的显示。

a.是 — 继续执行[步骤2](#step-2)。\
b.否 — 在[Adobe Commerce帮助中心知识库](https://support.magento.com/hc)中再次搜索相关搜索词。

+++

## 步骤2 — 检查安装问题 {#step-2}

+++**是Elasticsearch的新安装吗？**

a.是 — [确保Elasticsearch安装正确。](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md)同时检查您是否使用Adobe Commerce on cloud infrastructure 2.3.1或更高版本。 在云基础架构（版本2.3.1及更高版本）上升级到Adobe Commerce并且使用6.x之前的Elasticsearch版本的商家在部署时可能会遇到错误。 要解决此问题，Elasticsearch客户端模块和Elasticsearch服务需要采用最新的推荐版本。 有关步骤，请参阅Adobe Commerce在Cloud Infrastructure 2.3.1+升级后](/help/troubleshooting/elasticsearch/elasticsearch-issues-after-magento-commerce-cloud-2-3-1-upgrade.md)出现的[Elasticsearch问题。\
b. NO — 检查集群的运行状况。 如果您在Pro暂存或生产环境中，请运行此命令： `curl -m1 localhost:9200/_cluster/health?pretty`。 如果您在集成环境（包括所有Starter分支）中，请运行`curl -m1 elasticsearch.internal:9200/_cluster/health?pretty`。 继续执行[步骤3](#step-3)。

+++

## 步骤3 — 检查Elasticsearch群集是否可用 {#step-3}

+++**您是否收到服务响应？**

a.是 — 继续执行[步骤4](#step-4)。\
b.否 — 继续执行[步骤9](#step-9)。

+++

## 步骤4 — 验证Elasticsearch群集是否正常 {#step-4}

+++**绿色响应？**

a.是 — Elasticsearch可用于处理数据，重新编制索引应该有效。 继续执行[步骤5](#step-5)。\
b.否 — 黄色或红色表示节点之间的连接存在问题，并且某些数据可能不可用。 如果为黄色，请运行以下命令： `php bin/magento config:show catalog/search/engine`以检查您的搜索引擎。 继续执行[步骤6](#step-6)。 如果为红色，则[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步骤5 — 验证搜索是否有效 {#step-5}

+++**搜索问题？**

症状可能包括没有产品、类别空白或者产品或产品类别没有更新不正确。

a. YES — 运行此命令检查目录搜索的状态： `php bin/magento indexer:status`。 继续执行[步骤8](#step-8)。\
b.否 — 运行命令： `php bin/magento config:show catalog/search/engine`。 继续执行[步骤6](#step-6)。

+++

## 步骤6 — 检查ElasticSuite {#step-6}

+++**ElasticSuite正在使用中？**

a.是 — 通过运行此命令检查ElasticSuite是否为当前版本： `cat composer.lock | grep -A 1 elasticsuite | grep '"version"'`要检查此版本是否已弃用或推荐，请参阅[Github： Smile-SA/elaticsuite](https://github.com/Smile-SA/elasticsuite)。 如果ElasticSuite是最新的，请继续执行[步骤10](#step-10)。\
b.否 — 继续执行[步骤7](#step-7)。

+++

## 步骤7 — 检查ECE工具的最新状态 {#step-7}

+++**ECE-tools是否为最新版本？**

运行命令： `php ./vendor/bin/ece-tools -V`并检查ECE-tools版本。 它是[最新版本的ECE-tools](https://github.com/magento/ece-tools/releases)吗？

a.是 — 继续执行[步骤5a](#step-5)。\
b.否 — 将ECE-tools升级到最新版本。 运行命令`php bin/magento config: show catalog/search/engine`以检查您的搜索引擎。 继续执行[步骤6](#step-6)。

+++

## 步骤8 — 检查是否重新编制索引 {#step-8}

+++**目录搜索状态是否为&#x200B;_正在处理_？**

a.是 — 您需要等待处理完成，然后检查产品类别是否已更新。 如果没有，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 如果目录搜索的状态为&#x200B;_需要重新索引_，请在CLI/终端中运行： `php bin/magento cron:run`。 如果此项不起作用，请运行： `php bin/magento indexer:reindex`。 如果这样不能解决问题，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步骤9 — 检查yaml配置 {#step-9}

+++**`.yaml`文件最近已更新？**

a.是 — 通过引用DevDocs [设置Elasticsearch检查`.yaml`Elasticsearch配置：启用Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。\
b.否 — [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步骤10 — 检查跟踪索引 {#step-10}

+++**是否列出跟踪索引？**

运行`curl elasticsearch.internal:9200/_cat/indices` （如果您在包含所有入门分支的集成环境中）。 如果您在Pro暂存或生产环境中，请运行`curl localhost:9200/_cat/indices`。 是否列出跟踪索引？ 检查`_tracking_log_`的输出。

a.是 — 如果您使用的ElasticSuite版本低于2.8.0，建议您[升级到ElasticSuite 2.8.0以调整跟踪索引保留或禁用跟踪](https://support.magento.com/hc/en-us/articles/360035266131?)。 如果无法立即升级，您可以[创建cron以删除跟踪索引](/help/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.md)。 但是，这可能会导致性能问题。 升级到ElasticSuite 2.8.0或删除跟踪索引后，请运行命令（如果您在Pro暂存或生产环境中）：`localhost:9200/_cat/allocation?v`以检查可用空间。 如果您在一个集成环境（包括所有入门分支）上，请运行`elasticsearch.internal:9200/_cat/allocation?v`。 继续执行[步骤11](#step-11)。\
b.否 — 如果您在Pro暂存或生产环境中，请运行`localhost:9200/_cat/allocation?v`并检查可用空间。 如果您在一个集成环境（包括所有入门分支）上，请运行`elasticsearch.internal:9200/_cat/allocation?v`。 继续执行[步骤11](#step-11)。

+++

## 步骤11 — 查找特定错误 {#step-11}

+++**特定错误？**

Adobe Commerce和ES日志、扩展和自定义代码。

a.是 — 查看Adobe Commerce帮助中心故障排除文章[确保Elasticsearch安装正确](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md)或[Elasticsearch崩溃或在使用ElasticSuite插件时出现内存不足问题](https://support.magento.com/hc/en-us/articles/360035266131)。\
b.否 — 继续执行[步骤12](#step-12)。

+++

## 步骤12 — 检查可用存储 {#step-12}

+++**存储使用率> 85%？**

a.是 — 您需要增加可用存储。 请参阅DevDocs[设置Elasticsearch：启用Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。 然后运行： `localhost:9200/_cat/allocation?v`（如果您在Pro暂存或生产环境中）。 如果您在其中一个集成环境（包括所有Starter分支）上运行： `elasticsearch.internal:9200/_cat/allocation?v`。 继续执行[步骤11](#step-11)。\
b.否 — [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

[返回步骤1](#step-1)
