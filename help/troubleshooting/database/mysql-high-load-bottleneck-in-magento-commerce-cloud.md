---
title: 云基础架构上Adobe Commerce中的MySQL高负载瓶颈
description: 本主题讨论当MySQL的高负载导致Adobe Commerce在云基础架构上出现性能瓶颈问题的解决方案。
exl-id: c1f9d282-41d8-4850-8a24-336d55aa3140
feature: Cloud, Observability, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# 云基础架构上Adobe Commerce中的MySQL高负载瓶颈

本主题讨论当MySQL的高负载导致Adobe Commerce在云基础架构上出现性能瓶颈问题的解决方案。

## 受影响的产品和版本

* Adobe Commerce on cloud infrastructure 2.x.x，Pro客户。

### 先决条件

* ECE工具版本2002.0.16及更高版本
* New Relic APM服务(**您的Adobe Commerce on cloud infrastructure帐户包含New Relic APM服务的软件**&#x200B;以及许可证密钥。)

有关New Relic APM服务及其在Adobe Commerce on cloud infrastructure帐户中的设置的详细信息，请转到[New Relic服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service)和[New Relic APM简介](https://docs.newrelic.com/docs/apm/new-relic-apm/getting-started/introduction-apm/)。

## 问题

<u>查看问题是否影响您的步骤</u>

1. 在New Relic APM概述图表中，检查MySQL是否已变成瓶颈的第一个迹象。 请参阅下面的示例图片，其中MySQL已成为瓶颈，占用了大部分Web事务时间：

   ![KB-372_image002.png](assets/KB-372_image002.png)

   请注意图像中的红色虚线如何显示MySQL Web事务时间的明显上升趋势，然后在更高的级别达到峰值。
1. 然后，从此处，您可以转到&#x200B;**数据库**&#x200B;屏幕，在此屏幕中，您可以看到MySQL中高吞吐量或慢`SELECT`查询的第二个指示，并且在下面的示例图像中，您可以看到按&#x200B;**最耗时**&#x200B;排序时，您的存储（在此示例中）对`SELECT` MySQL查询的查询速度较慢。

   ![KB-372_image003_BlurredExtension.png](assets/KB-372_image003_BlurredExtension.png)

在New Relic APM中分析慢速事务。 如果您在MySQL数据库上看到大量查询或压力很大，则可以通过启用`SLAVE`连接将负载分散到不同的节点。

## 原因

云基础架构存储上的Adobe Commerce具有高吞吐量或在`SELECT` MySQL查询上速度较慢。

## 解决方案

>[!WARNING]
>
>对于缩放架构（拆分架构），不应启用Redis从属连接&#x200B;**&#x200B;**。 您可以通过转到项目URL （例如`https://console.adobecommerce.com/<owner-user-name>/<project-ID>/<environment-name>`）来检查您是否使用缩放的架构。 单击&#x200B;**[!UICONTROL SSH]**。 如果存在三个以上的节点，则表示您使用的是可扩展的架构。 如果在缩放的体系结构上启用Redis从属读取，则客户将在无法连接的Redis连接上收到错误。 这与群集如何配置为处理Redis连接有关。 Redis Slaves仍处于活动状态，但不会用于Redis Reads。 我们建议对扩展架构使用Adobe Commerce 2.3.5或更高版本，并实施新的Redis后端配置并为Redis实施L2缓存。

如果遇到这两个指示，为MySQL数据库和Redis启用`SLAVE`连接有助于将负载分散到不同的节点。

Adobe Commerce可以异步读取多个数据库或Redis。 通过将值`MYSQL_USE_SLAVE_CONNECTION`和`REDIS_USE_SLAVE_CONNECTION`设置为`true`来更新`.magento.env.yaml`文件，以使用到数据库的&#x200B;**只读**&#x200B;连接来接收非主节点上的只读流量。 这通过负载平衡提高了性能，因为只有一个节点需要处理读写通信。 设置为`false`可从`env.php`文件中删除任何现有的只读连接数组。

### 步骤

1. 编辑您的`.magento.env.yaml`文件，并添加以下内容：

   ![KB-372_image004.png](assets/KB-372_image004.png)

   您可以在DevDocs[&#128279;](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection)中的部署变量中找到更多详细信息。

1. 提交更改并推送更改。
1. 推送更改将启动新的部署过程。 成功完成部署后，您应该将云基础架构实例上的Adobe Commerce配置为使用从属连接。

## 常见问题

以下是当您考虑在云基础架构存储上为Adobe Commerce使用从连接功能时可能问到的常见问题。

* 使用从属连接是否存在任何已知问题或限制？ **使用从属连接时没有任何已知问题。 只需确保您使用的是最新更新的ece-tools包。 此处提供了有关如何更新ece-tools包[&#128279;](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)的说明。**
* 使用从属连接时是否会有额外的延迟？ *是的，跨可用区（跨可用区）延迟较高，在实例未过载且可以承担全部负载的情况下，会降低Adobe Commerce在云基础架构实例上的性能。 但很显然，如果实例过载，则主从节点可以通过将负载分散到MySQL数据库或Redis上的不同节点来帮助提高性能。*

  **在非重载群集上** - **从属连接将使性能降低10-15%**，这是不默认的原因之一。

  *但在重载群集上，性能会提高，因为通过流量减少负载可缓解这10-15%的负载。*
* 我应该为我的商店启用这些设置吗？ *如果MySQL数据库或Redis负载高或预期负载高，则绝对需要启用从属连接。 对于具有平均流量的常规客户，这是&#x200B;**不是**&#x200B;要启用的最佳设置。*

## 相关阅读

在我们的开发人员文档中：

* [部署变量](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy)。
* [设置可选的数据库复制](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/storage/split-db/multi-master-replication)。
* [ece-tools包](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview)。

>[!NOTE]
>
>我们知道，本文可能仍然包含行业标准的软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。
