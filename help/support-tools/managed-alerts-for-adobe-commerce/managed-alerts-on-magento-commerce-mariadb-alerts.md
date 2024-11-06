---
title: '在Adobe Commerce上管理警报：MariaDB警报'
description: '''本文提供了在New Relic中接收Adobe Commerce的MariaDB警报时的故障排除步骤。 MariaDB警报监控高查询负载以及过度的数据操作语言(DML)查询。 两者都可能导致用户体验降低甚至停机。 你可以收到四种警报：'
exl-id: 707e20e0-faba-4bcd-884c-b54568787442
feature: Cache, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# 在Adobe Commerce上管理警报：MariaDB警报

本文介绍了在New Relic中接收Adobe Commerce的MariaDB警报时的故障排除步骤。 MariaDB警报监控高查询负载以及过度的数据操作语言(DML)查询。 两者都可能导致用户体验降低甚至停机。 您可以接收四种警报：

* DML查询警告
* DML查询关键

## **受影响的产品和版本**

Adobe Commerce on cloud infrastructure Pro计划架构

## 问题

如果您已为New Relic](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)注册了[个托管警报，并且一个或多个警报阈值已超出，则您将在Adobe Commerce中收到托管警报。 这些警报由Adobe开发，旨在通过支持和工程部门的分析为客户提供一组标准。

**做！**

* 中止任何计划的部署，直到清除此警报。
* 如果您的网站处于或完全无响应，请立即将网站置于维护模式。 有关步骤，请参阅我们的开发人员文档中的[安装指南>启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。 确保将您的IP添加到免除IP地址列表，以确保您仍然能够访问站点进行故障排除。 有关步骤，请参阅[维护免除IP地址列表](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#instgde-cli-maint-exempt)。
* 结束任何脚本，例如导入，如果网站性能受到影响，则这些脚本可能会导致警报。

**不要！**

* 运行索引器或其他cron，这可能会对MariaDB造成额外压力。
* 执行任何主要管理任务(即Commerce管理、数据导入/导出)。
* 清除缓存。

## 解决方案

**DML查询(使用UPDATE、INSERT和DELETE修改数据库的查询)**

如果您在步骤1中收到“DML查询严重”警报，请启动该警报。 如果您在步骤2中收到了DML查询警告警报，请启动该警报。

1. 检查Adobe Commerce支持票证是否存在。 有关步骤，请参阅我们的知识库[跟踪您的支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)。 支持人员可能已收到New Relic阈值警报，创建了票证并开始处理此问题。 如果不存在票证，请创建一个。 票证应包含以下信息：
1. 联系原因：选择“已收到New Relic MariaDB警报”。
1. 警报的说明。
1. [New Relic事件链接](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents)。 这包含在您的[Adobe Commerce托管警报](/help/support-tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce.md)中。
1. 要确定问题的来源，请尝试识别DML查询：
1. 使用New Relic [APM UI页面>监控>数据库页面](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)中的步骤检查数据库操作。
1. 先按调用数排序，然后按操作排序。 查看INSERT、DELETE和UPDATE操作。
1. 寻找高平均。
1. 单击直达以查找数据库操作调用方。 这将按时间标识使用该查询的事务。
1. 寻找代码优化或操作优化：
1. 代码优化：寻求通过批量插入/更新、最大程度地减少索引使用或限制代码来优化查询。
1. 操作优化：卸载资源密集型数据修改以缩短通信时间。
1. 其他优化：确保您使用的是最新版本的ECE-Tools。 有关步骤，请参阅我们的开发人员文档中的[Cloud for Adobe Commerce >更新ece-tools版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)。

## 相关阅读

* 要研究其他常见的MariaDB问题，请参阅[云基础架构上Adobe Commerce最常见的数据库问题](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)。
* 要研究数据库最佳实践，请参阅[云基础架构上Adobe Commerce的数据库最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)。
