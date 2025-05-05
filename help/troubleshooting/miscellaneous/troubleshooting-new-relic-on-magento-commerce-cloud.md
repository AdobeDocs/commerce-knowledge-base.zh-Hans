---
title: New Relic云基础架构上的Adobe Commerce疑难解答
description: 本文提供用于对Adobe Commerce上的New Relic进行云基础架构故障诊断的资源。
exl-id: ea763291-5c9b-4575-b2ee-820dbc367743
feature: Cloud, Observability, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# New Relic云基础架构上的Adobe Commerce疑难解答

本文提供用于对Adobe Commerce上的New Relic进行云基础架构故障诊断的资源。

<table>
<tbody>
<tr>
<td class="wysiwyg-text-align-center"><strong>问题</strong></td>
<td class="wysiwyg-text-align-center"><strong>原因</strong></td>
<td class="wysiwyg-text-align-center"><strong>资源</strong></td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">访问问题</td>
</tr>
<tr>
<td>
<p><u>在New Relic中看不到项目。</u></p>
<p>您登录到<em>New Relic</em>，但看不到您应有权查看/访问的项目。</p>
</td>
<td>
<p>在这些情况下，管理员用户需要将您添加到项目中。</p>
</td>
<td>
<p><a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=zh-Hans">访问我们的支持知识库中的New Relic服务</a>。</p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">数据问题</td>
</tr>
<tr>
<td>
<p><u>安装后缺少数据。</u></p>
<p>使用<a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/new-relic-diagnostics">New Relic诊断实用程序</a>尝试找出原因。 如果这样没有帮助，请查看特定于代理的解决方案。 右侧列中提供了指向包含这些解决方案的文章的链接。</p>
</td>
<td>
<p>缺失数据可能由不同原因引起。 您可能需要：</p>
<ul>
<li>验证是否已安装代理。</li>
<li>验证您的应用程序名称和许可证密钥。</li>
<li>重新启动Web服务器。</li>
<li>确保您的系统符合兼容性要求。</li>
<li>ini设置。</li>
</ul>
</td>
<td>
<ul>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#apm-agents">New Relic文档&gt; APM代理&gt;看不到数据</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#browser-agent">New Relic文档&gt; New Relic浏览器&gt;看不到数据</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#infrastructure-agents">New Relic文档&gt; New Relic基础架构&gt;无数据</a></li>
<li><a href="https://docs.newrelic.com/docs/agents/manage-apm-agents/troubleshooting/not-seeing-data#mobile-agents">New Relic文档&gt; New Relic Mobile &gt;无数据</a></li>
</ul>
</td>
</tr>
<tr>
<td>
<p><u>交易时间戳不一致。</u>您可能很难使用New Relic UI找到时间较长的交易（超过5分钟）。 您还可能会发现所显示的事务超出了预期的时间范围。</p>
</td>
<td>
<p>New Relic UI显示交易结束的时间，而不是交易开始的时间。</p>
</td>
<td>
<p>要使用New Relic UI计算交易的开始，请检查交易的持续时间。 从New Relic UI提供的时间戳（交易结束）中减去持续时间量。</p>
</td>
</tr>
<tr>
<td>
<p>使用<code>|</code>和<code>%</code>等特殊字符的<u>NerdGraph GraphQL <code>curl</code>查询不起作用</u>。</p>
</td>
<td>
<p>NerdGraph中的New Relic“复制到curl”功能当前不提供处理特殊字符（如<code>|</code>和<code>%</code>）的方法。</p>
</td>
<td>
<p>使用不同的API库解决具有特殊字符的问题。 例如，用于Python上Graphql API的GraphQLClient库，或通过Java语言调用的Apache.commons。 查看<a href="https://graphql.org/code/">GraphQL</a>上的客户端库。</p>
</td>
</tr>
<tr>
<td>
<p><u>图表和功能板显示问题。</u></p>
</td>
<td>
<p>通过将New Relic域添加到允许列表或卸载导致问题的浏览器扩展来解决缺少的图表。</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/apm/new-relic-apm/troubleshooting/charts-missing-or-do-not-render">New Relic文档&gt;图表缺失或不呈现</a> </p>
</td>
</tr>
<tr>
<td class="wysiwyg-text-align-center" colspan="3">PHP代理问题</td>
</tr>
<tr>
<td>
<p><u>PHP代理未显示正确的实例计数。</u></p>
</td>
<td>
<p>实例的数量会根据后端进程和吞吐量而增加。 服务器值之间的差异可能是由一台服务器上运行的进程导致的，而不是另一台服务器上运行的进程导致的。</p>
</td>
<td>
<p><a href="https://docs.newrelic.com/docs/agents/php-agent/troubleshooting/troubleshoot-php-agent-instance-count">New Relic文档&gt; PHP代理实例计数疑难解答</a> </p>
</td>
</tr>
</tbody>
</table>
