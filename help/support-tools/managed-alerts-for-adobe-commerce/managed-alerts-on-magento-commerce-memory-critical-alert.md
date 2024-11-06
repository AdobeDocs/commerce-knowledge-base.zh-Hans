---
title: 'Adobe Commerce上的托管警报：内存严重警报'
description: 当您在New Relic中收到Adobe Commerce的内存严重警报时，本文介绍了故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。
exl-id: feed7998-c50b-4cbf-a92d-cbfc65745a1c
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Adobe Commerce上的托管警报：内存严重警报

当您在New Relic中收到Adobe Commerce的内存严重警报时，本文介绍了故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。

![磁盘严重警报](assets/memory-critical-magento-managed.png){width="500"}

## 受影响的产品和版本

云基础架构专业版上的所有Adobe Commerce版本都规划了架构。

## 问题

如果您已为New Relic](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)注册了[个托管警报，并且一个或多个警报阈值已超出，则您将在Adobe Commerce中收到托管警报。 这些警报由Adobe开发，旨在通过支持和工程部门的分析为客户提供一组标准。

<u> **做！** </u>

* 中止任何计划的部署，直到清除此警报
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅我们的开发人员文档中的[安装指南>启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅我们的开发人员文档中的[维护免除IP地址列表](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt)。

<u>**不要！**</u>

* 启动其他营销活动，这可能会给您的网站带来其他页面查看次数。
* 运行索引器或其他cron，这可能会在CPU或磁盘上造成额外压力。
* 执行任何主要管理任务(即Commerce管理、数据导入/导出)。
* 清除缓存。

如果您在调查并解决警报原因之前执行了任何“不响应”操作，则您的网站可能会变得无响应（如果您尚未经历网站中断）。

## 解决方案

按照以下步骤确定原因并排除故障。

>[!WARNING]
>
>由于这是一个严重警报，强烈建议您在尝试排查问题（从步骤2开始）之前完成&#x200B;**步骤1**。

1. 检查Adobe Commerce支持票证是否存在。 有关步骤，请参阅我们的支持知识库中的[跟踪您的支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)。 支持人员可能已经收到New Relic阈值警报，创建了票证并开始处理此问题。 如果不存在票证，请创建一个。 票证应包含以下信息：
   * 联系原因：选择“已收到New Relic严重警报”
   * 警报描述
   * [New Relic事件链接](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 这包含在您的[Adobe Commerce托管警报](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)中。

1. 使用[New Relic APM的“基础结构”页](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)识别占用大量内存的进程。 有关步骤，请参阅New Relic [基础架构监视主机页面>进程选项卡](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)：
   * 如果Redis、MySQL或PHP等服务是内存消耗的主要来源，请尝试以下操作：
1. 检查您是否使用最新版本。 较新版本有时可以修复内存泄漏。 如果您不是最新版本，请考虑升级。 有关步骤，请参阅我们的开发人员文档中的[Adobe Commerce on cloud infrastructure > Services > Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html)。
1. 如果服务问题与版本无关，请尝试以下操作：
1. **MySQL**：检查长时间运行的查询、未定义主键以及重复索引等问题。 有关步骤，请参阅我们的支持知识库中的[Adobe Commerce中关于云基础架构的最常见数据库问题](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)。
1. **Redis**：如果Redis是内存消耗的最大来源，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。
1. **PHP**：如果PHP是内存消耗的最大来源，请在CLI/终端中运行`ps aufx`来检查正在运行的进程。 在终端输出中，您将看到当前正在执行的cron作业和进程。 检查进程执行时间的输出。 如果存在执行时间较长的cron，则该cron可能会挂起。 有关故障排除步骤，请参阅我们的支持知识库中的[性能缓慢、运行缓慢且时间较长](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)和[Cron作业停留在“正在运行”状态](https://support.magento.com/hc/en-us/articles/360033099451)。
1. 如果您仍在努力识别问题的根源，请使用[New Relic APM的“事务”页](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)识别具有性能问题的事务：
   * 按升序Apdex分数对事务排序。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)指用户对Web应用程序和服务的响应时间的满意度。 [低Apdex分数](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce-apdex-warning-alert.md)可能表示瓶颈（响应时间较长的事务）。 通常是数据库、 Redis或PHP。 有关步骤，请参阅New Relic [查看Apdex满意度最高的事务](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)。
   * 按最高吞吐量、最慢的平均响应时间、最耗时的阈值和其他阈值对事务进行排序。 有关步骤，请参阅New Relic [查找具体性能问题](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。 如果您仍在努力找出问题，请使用New Relic APM的“基础架构”页面。
1. 如果您无法确定内存消耗增加的原因，请查看近期趋势以确定近期代码部署或配置更改（例如，新客户组和目录的大幅更改）中存在的问题。 建议您查看过去7天的活动，以了解代码部署或更改中的任何关联。
1. 如果上述方法不能帮助您在合理的时间内找到原因和/或解决方案，请请求升级站点，或将站点置于维护模式（如果尚未这样做）。 有关步骤，请参阅我们的支持知识库中的[如何请求临时调整大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md)，以及我们的开发人员文档中的[安装指南>启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。
1. 如果Upsize使站点恢复正常运营，请考虑请求永久升级(联系您的Adobe客户团队)，或尝试通过运行负载测试和优化查询或在专用暂存中重现问题，或尝试运行降低服务压力的代码。 请参阅我们的开发人员文档中的[云基础架构上的Adobe Commerce >测试部署>负载和压力测试](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing)。
