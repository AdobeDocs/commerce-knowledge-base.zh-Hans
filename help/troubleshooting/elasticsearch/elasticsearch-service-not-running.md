---
title: Elasticsearch服务未运行
description: 本文提供了在Elasticsearch(ES)服务未运行（通常是因为崩溃）时可能遇到的错误的解决方案。 症状可能包括使用curl运行运行状况检查时的错误、使用命令行重新编制索引、异常和PHP错误以及产品页面上的错误。 该表列出了错误以及尝试解决这些错误的资源的链接。 一个症状可能由多种不同原因引起。
exl-id: 2c2230de-cb30-4a03-8c3e-d9f44783dbae
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Elasticsearch服务未运行

本文提供了在Elasticsearch(ES)服务未运行（通常是因为崩溃）时可能遇到的错误的解决方案。 症状可能包括使用curl运行运行状况检查时的错误、使用命令行重新编制索引、异常和PHP错误以及产品页面上的错误。 该表列出了错误以及尝试解决这些错误的资源的链接。 一个症状可能由多种不同原因引起。

## Elasticsearch版本与Adobe Commerce的兼容性

* Adobe Commerce内部部署和Adobe Commerce on cloud基础架构：

   * v2.2.3+支持ES 5.x
   * v2.2.8+和v2.3.1+支持ES 6.x
   * 由于[生命周期结束](https://www.elastic.co/support/eol)，不建议使用ES v2.x和v5.x。 但是，如果您使用的是Adobe Commerce v2.3.1并且要使用ES 2.x或ES 5.x，您必须[更改Elasticsearchphp客户端](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/search/overview-search)。

* Magento Open Sourcev2.3.0+支持ES 5.x和6.x （但建议使用6.x ）。

<table>
<tr>
<th>ES服务未运行时的症状</th>
<th>详细信息</th>
<th>资源</th>
</tr>
<tr>
<td rowspan="3">异常错误</td>
</tr>
<tr>
<td>
<code>&lbrace;"0":"&lbrace;\"error\":&lbrace;\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}&rbrack;</code>
</td>
<td>
已配置<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsearch-5-is-configured-but-search-page-does-not-load-with-fielddata-is-disabled...-error.html?lang=zh-Hans">Elasticsearch5，但我们的支持知识库中未加载包含“Fielddata已禁用……”错误</a>的搜索页面。
</td>
</tr>
<tr>
<td>
<code>Elasticsearch\Common\Exceptions\NoNodesAvailableException: Noticed exception 'Elasticsearch\Common\Exceptions\NoNodesAvailableException' with message 'No alive nodes found in your cluster' in /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/ConnectionPool/StaticNoPingConnectionPool.php:51</code>
</td>
<td>
未删除Elasticsuite索引。  查看我们的支持知识库中的<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=zh-Hans">ElasticSuite跟踪索引导致Elasticsearch</a>出现问题。
 </td>
</tr>
<tr>
<td>PHP错误</td>
<td>
<i>在您的群集中未找到活动节点"，"1"："#0 /app/&lt;projectid&gt;/vendor/elasticsearch/elasticsearch/src/Elasticsearch/Transport.php</i>
</td>
<td rowspan="4">
<ul>
<li>磁盘空间不足的资源：<ul>
<li><a href="https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk/">解决Linux和Unix系统硬盘问题（如磁盘已满或无法写入磁盘）的8个提示</a></li>
<li><a href="https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not">serverfault： df表示磁盘已满，但磁盘未满</a></li>
<li><a href="https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux">unix.stackexchange.com：跟踪Linux上的磁盘空间占用情况？</a></li>
<li>日志文件没有足够定期存档。 请参阅我们的开发人员文档中的<a href="https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/action-logs/action-log-archive">配置日志存档</a>。</li>
<li>文件系统目录未优化。 请参阅我们的开发人员文档中的<a href="https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/tools/developer-tools#resource-file-optimization">文件优化</a>。</li>
<li>如果上述文档中的解决方案不能解决此问题，请考虑联系您的Adobe客户团队以请求更多存储空间。</li>
</ul>
</li>
<li>如果磁盘尚未用完存储空间，但左栏中仍显示错误消息，请<a href="/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket">提交支持票证</a>。</li>
</ul>
<ul>
<li>查看我们的支持知识库中的<a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/elasticsuite-tracking-indices-causes-problems-with-elasticsearch.html?lang=zh-Hans">ElasticSuite跟踪索引导致Elasticsearch</a>出现问题。
</li>
</ul>
</td>
</tr>
<tr>
<td><code>Curl</code> 错误</td>
<td>运行<code>curl</code>命令以检查Elasticsearch运行状况：<code>curl -m1 localhost:9200/_cluster/health?pretty</code>（或<code>curl -m1 elasticsearch.internal:9200/_cluster/health?pretty</code>Starter帐户）会产生以下错误： <i>错误： curl： (7)无法连接到本地主机端口9200：连接被拒绝</i> </td>
</tr>
<tr>
<td>命令行错误</td>
<td>运行<code>$ bin/magento indexer:reindex catalogsearch_fulltext</code>将生成此错误<i>目录搜索索引器进程未知错误：
        在您的群集中未找到活动节点</i>
</td>
</tr>
<tr>
<td>产品页面错误
</td>
<td><i>处理您的请求时出错。
      出于安全原因，默认情况下禁用异常打印</code></i>
</tr>
</table>
