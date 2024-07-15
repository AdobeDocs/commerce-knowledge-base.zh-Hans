---
title: Adobe Commerce的受管警报
description: 如果您是Adobe Commerce on cloud infrastructure Pro规划架构客户，则可以使用受管警报了解站点的运行状况。 如果您是Adobe Commerce on cloud infrastructure入门计划架构客户，则只会收到关于Apdex和错误率情况的警报。
exl-id: 4d08eaad-a3ce-4f6c-9c32-58e44e1d6534
feature: Observability, Support, Tools and External Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# Adobe Commerce的受管警报


我们设置了关键的仪表板和警报，帮助您了解您的站点何时达到关键存储和Apdex级别（用户对应用程序和服务响应时间的满意度）。 这有助于您在发现响应时间缓慢或中断之前采取行动。 您将能够使用下面列出的文章对警报进行故障排除。 在使用警报之前，请先设置通知渠道。 请参阅我们的开发人员文档中的[New Relic配置通知渠道](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)。

>[!NOTE]
>
>如果Adobe Commerce警报策略的托管警报不可用，可能是由于此帐户是新创建的或最近配置了New Relic。 在每个星期二运行一个进程，将警报策略添加到这些帐户。 警报策略应在下一个进程运行后的第二天可供您使用。 如果策略仍然缺失，请[提交Adobe Commerce支持请求](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket)并包含您的项目ID。

请参阅下表中的链接，这些链接指向提供这些警报的故障诊断步骤的知识库文章：

* Adobe Commerce的受管警报：CPU警告警报
* Adobe Commerce的受管警报：CPU严重警报
* Adobe Commerce托管警报：内存警告警报
* Adobe Commerce的受管警报：内存严重警报
* Adobe Commerce的受管警报：Apdex警告警报
* Adobe Commerce的受管警报：Apdex严重警报
* Adobe Commerce托管警报：磁盘警告警报
* Adobe Commerce的受管警报：磁盘严重警报
* 在Adobe Commerce上管理警报：MariaDB警报
* Adobe Commerce上的托管警报： Redis内存警告警报
* Adobe Commerce上的托管警报：Redis内存严重警报

>[!NOTE]
>
>“警告警报”和“严重警报”的设置阈值基于我们正在使用客户群的历史性能数据进行的研究结果，它代表了Adobe Commerce支持和工程团队的最新见解。 请注意，根据最新的持续分析，这些阈值可能会发生更改。 典型的警报流程是接收警报的严重性从低到高。 因此，在收到“严重”警报之前，您可能会收到“警告”警报。 有关疑难解答步骤，请参阅文章链接。

<table style="width: 128.434%; height: 660px;" width="100%">
<tbody>
<tr style="height: 44px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 44px;">
<p><strong>严重程度</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 44px;">
<p><strong>CPU</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 44px;">
<p><strong>内存</strong></p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 44px;">
<p><strong>磁盘</strong></p>
</td>
<td class='"wysiwyg-text-align-center wysiwyg-text-align-center' style="width: 9%; height: 44px;">
<p><strong>Apdex</strong></p>
</td>
<td style="width: 7.058036%; height: 44px;">
<p><strong>MariaDB</strong></p>
</td>
<td class="wysiwyg-text-align-center med-col">
<p><strong>Redis内存</strong></p>
</td>
<td class="wysiwyg-text-align-center large-col" style="width: 24.5638%; height: 44px;">
<p><strong>疑难解答文章</strong></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md">Adobe Commerce的受管警报：CPU警告警报</a><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-cpu-warning-alert.md"></a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">关键</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-cpu-critical-alert.md">Adobe Commerce的受管警报：CPU严重警报</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-memory-warning-alert.md">Adobe Commerce托管警报：内存警告警报</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">关键</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;">
<p> </p>
<p>✅</p>
</td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-memory-critical-alert.md#_critical_memory">Adobe Commerce的受管警报：内存严重警报</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md">Adobe Commerce的受管警报：Apdex警告警报</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">关键</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;">✅</td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-critical-alert.md">Adobe Commerce的受管警报：Apdex严重警报</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">警告</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-warning-alert.md">Adobe Commerce托管警报：磁盘警告警报</a></p>
</td>
</tr>
<tr style="height: 66px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 66px;">关键</td>
<td class="wysiwyg-text-align-center" style="width: 6.14286%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 10.5714%; height: 66px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 7.14286%; height: 66px;">✅</td>
<td class="wysiwyg-text-align-center" style="width: 9%; height: 66px;"> </td>
<td style="width: 0.058036%; height: 66px;"> </td>
<td style="width: 24.5638%; height: 66px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 66px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md" title="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-disk-critical-alert.md">Adobe Commerce的受管警报：磁盘严重警报</a></p>
</td>
</tr>
<tr style="height: 44px;">
<td style="width: 17.8571%; height: 44px;">警告和严重</td>
<td style="width: 6.14286%; height: 44px;"> </td>
<td style="width: 10.5714%; height: 44px;"> </td>
<td style="width: 7.14286%; height: 44px;"> </td>
<td style="width: 9%; height: 44px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 44px;">✅</td>
<td style="width: 24.5638%; height: 44px;">
<p> </p>
</td>
<td style="width: 24.5638%; height: 44px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-mariadb-alerts.md">在Adobe Commerce上管理警报：MariaDB警报</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">警告</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-warning-alert.md">Adobe Commerce上的托管警报： Redis内存警告警报</a></p>
</td>
</tr>
<tr style="height: 22px;">
<td class="wysiwyg-text-align-center" style="width: 17.8571%; height: 22px;">关键</td>
<td style="width: 6.14286%; height: 22px;"> </td>
<td style="width: 10.5714%; height: 22px;"> </td>
<td style="width: 7.14286%; height: 22px;"> </td>
<td style="width: 9%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 0.058036%; height: 22px;"> </td>
<td class="wysiwyg-text-align-center" style="width: 24.5638%; height: 22px;">
<p>✅</p>
</td>
<td style="width: 24.5638%; height: 22px;">
<p><a href="/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-on-magento-commerce-redis-memory-critical-alert.md">Adobe Commerce上的托管警报：Redis内存严重警报</a></p>
</td>
</tr>
</tbody>
</table>
