---
title: Adobe Commerce 2.4.0中将删除MySQL目录搜索引擎
description: Adobe Commerce内部部署、Adobe Commerce on cloud infrastructure和Magento Open Source2.4.0将在未来几个月发布。 对于Adobe Commerce内部部署和Magento Open Source版本2.4.0，Elasticsearch6.x或7.x将是必需组件，并且将删除MySQL搜索引擎。 在云基础架构上的Adobe Commerce中，已需要Elasticsearch。
exl-id: 717be515-3cbf-42e9-9b72-caf11b8c3771
feature: Catalog Management, Search, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# Adobe Commerce 2.4.0中将删除MySQL目录搜索引擎

Adobe Commerce内部部署、Adobe Commerce on cloud infrastructure和Magento Open Source2.4.0将在未来几个月发布。 对于Adobe Commerce内部部署和Magento Open Source版本2.4.0，Elasticsearch6.x或7.x将是必需组件，并且将删除MySQL搜索引擎。 在云基础架构上的Adobe Commerce中，已需要Elasticsearch。

>[!WARNING]
>
>在尝试升级之前未能安装/配置Elasticsearch6/7可能会导致严重的Adobe Commerce问题。 请注意，如果没有48个工作小时的通知，就无法将云基础架构上Adobe Commerce上的服务升级推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产前48小时[提交支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，其中详细列出所需的服务升级并指明希望升级过程开始的时间。

删除MySQL搜索引擎的原因是，Elasticsearch提供了优异的搜索功能以及目录性能优化。

## 受影响的产品和版本：

* Adobe Commerce内部部署v2.4.0
* Magento Open Sourcev2.4.0

## 升级：

<table style="height: 164px; width: 632.2px;">
<tbody>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;"><strong>搜索引擎</strong></td>
<td class="wysiwyg-text-align-center" style="width: 478.2px;"><strong>操作</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">MySQL</td>
<td style="width: 478.2px;">您必须安装Elasticsearch。 请参阅我们的开发人员文档中的<a href="https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/search/overview-search">安装和配置Elasticsearch</a>。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch（未列出版本）</td>
<td style="width: 478.2px;">您使用的是Elasticsearch2，必须更新为Elasticsearch7（首选）或6。 有关详细信息，请参阅开发人员文档中的<a href="https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/search/overview-search#es-upgrade6">升级Elasticsearch</a>和<a href="https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/search/configure-search-engine">配置Commerce以使用Elasticsearch</a>。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">ELASTICSEARCH5</td>
<td style="width: 478.2px;">Elasticsearch5的<a href="https://www.elastic.co/support/eol">生命周期已结束</a>，已在Adobe Commerce 2.4.0中弃用。更新至Elasticsearch7（首选）或6。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">Elasticsearch6或7</td>
<td style="width: 478.2px;">在升级到Adobe Commerce 2.4.0之前，您无需执行任何其他步骤。</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" style="width: 133px;">第三方扩展</td>
<td style="width: 478.2px;">您无需安装Elasticsearch。 Adobe Commerce建议您联系搜索引擎供应商，以确定您的扩展是否与Adobe Commerce 2.4.0完全兼容。</td>
</tr>
</tbody>
</table>

## 安装：

在发布Adobe Commerce内部部署和Magento Open Source2.4.0时，Elasticsearch将是一个必需组件，因此您必须先设置并配置Elasticsearch主机，然后才能安装版本2.4.0。请参阅我们的开发人员文档中的[安装和配置Elasticsearch](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/search/overview-search)。

默认情况下，Adobe Commerce搜索将使用Elasticsearch7作为搜索引擎，并尝试连接到localhost：9200上的服务器。 还支持Elasticsearch6.x。 如果配置与默认值不匹配，则可以使用传递给`setup:install`的参数配置这些设置，其方式与配置数据库连接的方式大致相同。

例如，`setup:install --elasticsearch-host=es.mystore.com`

在安装期间，将检查Elasticsearch连接，如果Adobe Commerce无法连接到Elasticsearch主机，安装将失败。 如果发生这种情况，请检查您的Elasticsearch是否已启动并正在运行，以及您提供的连接参数是否正确。
