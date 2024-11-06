---
title: Adobe Commerce cloud基础架构2.3.1+升级后的Elasticsearch问题
description: 如果您使用的是Elasticsearch版本2.x和5.x，本文将讨论在云基础架构版本2.3.1及更高版本上升级到Adobe Commerce后修复部署期间出现的问题。
exl-id: 6ceeb2ea-528d-4c03-ab2b-c5aed46fd0a2
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Adobe Commerce cloud基础架构2.3.1+升级后的Elasticsearch问题

>[!WARNING]
>
>将在Adobe Commerce 2.4.0](/help/announcements/adobe-commerce-announcements/mysql-catalog-search-engine-will-be-removed-in-magento-2-4-0.md)中删除[MySQL目录搜索引擎。 在安装版本2.4.0之前，必须设置并配置Elasticsearch主机。请参阅[安装和配置Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)。

>[!WARNING]
>
>请注意，如果不提前48个工作小时通知我们的基础架构团队，则无法将服务升级推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产前48小时[提交支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，其中详细列出所需的服务升级并指明希望升级过程开始的时间。

如果您使用的是Elasticsearch版本2.x和5.x，本文将讨论在云基础架构版本2.3.1及更高版本上升级到Adobe Commerce后修复部署期间出现的问题。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.3.1+
* Elasticsearch2.x和5.x

## 原因

在云基础架构（版本2.3.1及更高版本）上升级到Adobe Commerce并且使用6.x之前的Elasticsearch版本的商家在部署时可能会遇到错误。 这是因为Elasticsearch版本2.x和5.x的生命周期已结束[并且在Adobe Commerce中不再受支持。 ](https://www.elastic.co/support/eol)Elasticsearch客户端必须是最新的，或者运行部署可能会触发错误。 要了解更多信息，请参阅我们的开发人员文档中的[更改Elasticsearch客户端](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)。

## 问题

在部署时，您会看到类似于以下内容的错误消息，指示您的Elasticsearch版本不兼容：基础结构层上的&#x200B;*Elasticsearch服务版本5.2.2与Magento应用程序使用的elasticsearch/elasticsearch module (6.7.0.0)的当前版本不兼容。* *您可以通过将Magento云基础架构上的Elasticsearch服务升级到版本6.x*&#x200B;来修复此问题。 此问题的其他症状可能是缺少图像，以及环境中的过滤器出现问题。

## 解决方案

>[!WARNING]
>
>如果您拥有共享环境，请确保暂存和生产环境已准备好升级。

要解决此问题，Elasticsearch客户端模块和Elasticsearch服务需要采用最新的推荐版本：

1. 按照我们的开发人员文档中的说明[更改Elasticsearch模块](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)，以便您拥有最新推荐版本的Elasticsearch客户端模块。
1. [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)并请求在暂存和生产环境中将Elasticsearch服务更新为6.x。 请注意，Elasticsearch服务的升级可能需要一些时间才能完成。

## 相关阅读

* 在开发人员文档中[Adobe Commerce 2.3技术栈栈要求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview)。
* 在开发人员文档中[设置Elasticsearch服务](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。
* 在我们的开发人员文档中[安装和配置Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)。
* [确保已在我们的支持知识库中正确安装Elasticsearch](/help/troubleshooting/elasticsearch/ensure-elasticsearch-is-installed-properly.md)。
