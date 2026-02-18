---
title: 使用Adobe Commerce上的New Relic排除性能故障
description: 本文介绍了使用New Relic解决Adobe Commerce云基础架构性能问题的故障排除步骤。 它还提供了获取进一步信息的资源。 以下是问题列表。 单击查看我们的支持知识库中的故障排除步骤：
exl-id: 0a22beb7-18b0-47eb-a6b8-63b7322b392c
feature: Observability
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# 使用Adobe Commerce上的New Relic排除性能故障

本文介绍了使用New Relic解决Adobe Commerce云基础架构性能问题的故障排除步骤。 它还提供了获取进一步信息的资源。 下表包含推荐资源的以下问题：

* Apdex得分低
* CPU使用率较高
* 高输入/输出操作
* 中断

<table>
<tbody>
<tr>
<td>问题</td>
<td>故障排除</td>
<td>资源</td>
</tr>
<tr>
<td>
<p>Apdex得分低：</p>
<p>您的New Relic <a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measuring-user-satisfaction">Apdex得分</a>衡量用户对Web应用程序和服务的响应时间的满意度。</p>
</td>
<td>
<p>您登录到<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt;概述。 在“概述”页面的右侧，您会看到Apdex得分图。 Apdex得分为0.5或以下是一个值得关注的问题，需要调查：Web事务时间（服务器请求）：</p>
<ol>
<ol>
<li>登录到<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; （选择应用程序） &gt;概述。 确保在主图表下拉过滤器上将过滤器设置为Web事务时间。 在“事务”表的下方，查找应用程序服务器时间。 验证是否有任何长期运行或可疑的交易。</li>
<li>通过转至“监控”&gt;“事务”逐个调查，并确保为Web和最耗时的<em>.</em>设置筛选器
</li>
<li>然后搜索使用资源的第三方模块：支付提供商、ERP等。</li>
<li>在APM的“监视”部分中：<ol>
<li>单击“事务”。</li>
<li>向下滚动，单击显示所有事务表。</li>
<li>您可以按<a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#table_view">各种参数</a>对事务进行排序，并跳转到引起怀疑的事务。</li>
<li>查看Apdex得分低、Count异常高或Avg时间长或Dissat %的事务。</li>
<li>单击每个单独的事务。 如果无法解决此问题，请<a href="https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket">提交支持票证。</a>
</li>
<li>如果需要进一步调查，请考虑检查非Web事务。</li>
</ol>
</li>
</ol>
</ol>
<p>非Web事务时间（操作和后台任务）：</p>
<ol>
<ol>
<li>登录到<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt; （选择应用程序） &gt;概述。 确保在主图形下拉过滤器中选择非Web事务时间。 单击“事务处理”表中的单个事务处理。 查找长期运行或可疑的交易。 这包括后端作业、cron作业或导入/导出作业（包括第三方作业）。</li>
</ol>
</ol>
</td>
<td>
<p>要了解有关New Relic Apdex得分的更多信息，请参阅<a href="https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction">New Relic文档&gt; APM Apdex &gt;衡量用户满意度</a>。 您还可以在我们的支持知识库中参考<a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce-apdex-warning-alert">Adobe Commerce托管警报：Apdex警告警报</a>。</p>
</td>
</tr>
<tr>
<td>
<p>CPU使用率较高：</p>
<p>CPU使用率高可能表示服务特别忙，如MySQL、Redis等。</p>
</td>
<td>
<ol>
<li>登录到<a href="https://login.newrelic.com/login">New Relic</a> &gt;基础架构&gt;进程。</li>
<li>查看CPU图形以了解是否存在任何占用超过100% CPU时间的停滞或高耗时的进程，并与实例上的处理器计数进行比较。 请注意资源利用率的高峰。 不建议您终止进程，除非该进程处于卡住状态。</li>
</ol>
</td>
<td>
<p>要了解有关性能指标的更多信息，特别是CPU百分比、I/O字节数和单个进程或进程组的内存使用情况，请参阅<a href="https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes">New Relic文档&gt;基础架构UI页面&gt;基础架构主机页面&gt;进程选项卡</a>。</p>
</td>
</tr>
<tr>
<td>
<p>高I/O操作：对于每个客户，此数字将各不相同，但会与平均值有显着差异。</p>
</td>
<td>
<p>与以前的平均I/O操作相比，请寻找不寻常的峰值：</p>
<ol>
<li>登录到<a href="https://login.newrelic.com/login">New Relic</a> &gt;基础架构&gt;进程。</li>
<li>查看“I/O每秒读取字节数”图表。</li>
<li>记录尖峰的时间。</li>
<li>单击APM。</li>
<li>确保在主图形下拉过滤器中选择Web事务时间。</li>
<li>设置您记录的尖峰时间的时间。</li>
<li>搜索导致高I/O操作的事务。</li>
<li>深入到每个交易跟踪&gt;跟踪详细信息，以找到可能导致问题的原因。</li>
</ol>
</td>
</tr>
<tr>
<td>
<p>服务中断：New Relic按Apdex确定服务中断。 在Apdex得分图表上，您将看到一条红线，指示Apdex &lt; 0.4（被视为中断）。</p>
</td>
<td>
<p>调查中断可能需要几个步骤，包括检查Web和非Web事务、数据库和第三方事务。 Web事务：</p>
<ol>
<li>登录到<a href="https://login.newrelic.com/login">New Relic</a> &gt; APM &gt;概述。 确保在下拉图形过滤器上将该过滤器设置为Web事务时间。</li>
<li>手动缩小时间范围。</li>
<li>单击“事务”。 确保将过滤器设置为Web且最耗时。 调查运行时间最长的事务处理。</li>
<li>如果需要进一步调查，请考虑检查非Web事务。</li>
</ol>
<p>非Web事务：</p>
<ol>
<li>返回概述页面，然后在下拉筛选器中切换到非Web事务。</li>
<li>逐一查看页面最底部的事务跟踪。</li>
<li>根据问题而定，您可能需要使用第三方工具（如PHP探查器）来查找瓶颈。</li>
<li>如果需要进一步调查，请考虑检查数据库进程。</li>
</ol>
<p>数据库进程：</p>
<ol>
<li>在“APM”页上，转到“监视”&gt;“数据库”。</li>
<li>按最耗时的内容排序。</li>
<li>查看热门查询。

注意： <code>更新</code> 或<code>插入</code>查询是使用CPU最多的查询。</li>
<li>从排序依据选择器切换到吞吐量，并查找导致数据库吞吐量下降的进程。</li>
<li>如果需要进一步调查，请考虑检查第三方服务。</li>
</ol>
<p>第三方服务：</p>
<ol>
<li>在APM页面上，转到监控&gt;外部服务。</li>
<li>从排序依据下拉列表中选择最慢的平均响应时间。</li>
<li>查找就在停机之前发生的流程。</li>
</ol>
</td>
<td>
<p>要了解有关调查特定性能问题的更多信息，请参阅<a href="https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems#tx_functions">New Relic文档&gt; APM UI页面&gt;事务页面&gt;使用向下钻取函数</a>。</p>
</td>
</tr>
</tbody>
</table>
