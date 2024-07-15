---
title: 'Adobe Commerce托管警报：CPU警告警报'
description: 当您在New Relic中收到Adobe Commerce的CPU警告警报时，本文介绍了故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。
exl-id: 03686684-3b7e-430a-a05a-a96f38345322
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Adobe Commerce的受管警报：CPU警告警报

当您在New Relic中收到Adobe Commerce的CPU警告警报时，本文介绍了故障排除步骤。 需要立即采取措施来解决问题。 根据您选择的警报通知渠道，警报将类似于以下内容。

![CPU警告警报](assets/cpu-warning-magento-managed.png){width="500"}

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure Pro计划架构

## 问题

如果您已为New Relic](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)注册了[托管警报，并且一个或多个警报阈值已超出，则您将在Adobe Commerce中收到警报。 这些警报由Adobe开发，旨在通过支持和工程部门的分析为客户提供一组标准。

<u> **做！** </u>

* 中止任何计划的部署，直到清除此警报。
* 如果您的网站完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅我们的开发人员文档中的[安装指南>启用或禁用维护模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅我们的开发人员文档中的[维护免除IP地址列表](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten#instgde-cli-maint-exempt)。

<u>**不要！**</u>

* 启动其他营销活动，这可能会给您的网站带来其他页面查看次数。
* 运行索引器或其他cron，这可能会在CPU或磁盘上造成额外压力。
* 执行任何主要管理任务(即Commerce管理、数据导入/导出)。
* 清除缓存。

## 解决方案

按照以下步骤确定原因并排除故障。

1. 使用[New Relic APM的“事务”页](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)识别具有性能问题的事务：
   * 按升序Apdex分数对事务排序。 [Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)指用户对Web应用程序和服务的响应时间的满意度。 [Apdex得分低](/help/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.md#low_user_satisfaction)可能表示存在瓶颈（响应时间较长的事务）。 通常是数据库、 Redis或PHP。 有关步骤，请参阅New Relic [查看Apdex满意度最高的事务](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)。
   * 按最高吞吐量、最慢的平均响应时间、最耗时的阈值和其他阈值对事务进行排序。 有关步骤，请参阅New Relic [查找具体性能问题](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems)。
1. 如果您仍在努力识别源，请使用[New Relic APM的“基础架构”页面](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/)来识别资源密集型服务。 有关步骤，请参阅New Relic [基础架构监视主机页面>进程选项卡](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes)。
1. 如果标识了源，请通过SSH连接到环境以进一步调查。 有关步骤，请参阅我们的开发人员文档中的[Cloud for Adobe Commerce > SSH到您的环境](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh)。
1. 如果你还在努力找出问题的根源：
   * 查看最近的趋势，以确定最近的代码部署或配置更改（例如，新客户组和目录的大幅更改）中存在的问题。 建议您查看过去七天的活动，以了解代码部署或更改中的任何关联。
   * 考虑检查和禁用平面目录。 有关步骤，请参阅我们的支持知识库中的[性能缓慢、运行缓慢且长时间的crons](/help/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons.md)。
   * 如果您怀疑正在遭受DDoS攻击，请尝试阻止机器人流量。 有关步骤，请参阅我们的支持知识库中的[如何阻止Adobe Commerce在Fastly级别](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md)的恶意流量。
1. 如果问题看起来是暂时性的，请执行缓解步骤（如升级）或将站点置于维护模式。 有关步骤，请参阅我们的支持知识库中的[如何请求临时调整大小](/help/how-to/general/how-to-request-temporary-magento-upsize.md)，以及开发人员文档中的[安装指南>启用或禁用维护模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=mainten)。 如果Upsize将站点恢复为正常运营，请考虑请求永久升级(联系您的Adobe客户团队)，或尝试通过运行负载测试和优化查询或在专用暂存中重现问题，或运行降低服务压力的代码。 有关步骤，请参阅我们的开发人员文档中的[Cloud for Adobe Commerce >测试部署>负载和压力测试](https://devdocs.magento.com/cloud/live/stage-prod-test.html#loadtest)。
