---
title: 与Adobe Commerce上max_allowed_packet相关的数据库错误
description: 本文针对“var/log/exception.log”中的数据库连接错误，提供了一种解决方案，在导入大量产品或执行其他任务以强制服务器处理大于“max_allowed_packet”中设置的大于默认值16MB的数据包时，可能会发生这种错误。
exl-id: e8932b72-91a3-43ea-800e-a6c7a5a17656
feature: Best Practices, Observability, Services
role: Developer
source-git-commit: 5ca7a4400e62db2419b32a31a4f6cf04f5a82e35
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# 与Adobe Commerce上max_allowed_packet相关的数据库错误

本文为导入大量产品或执行其他任务强制服务器处理大于`var/log/exception.log`中设置的大于默认值16MB的数据包时，`max_allowed_packet`中可能发生的数据库连接错误提供了解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署，所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

当[!DNL MySQL]客户端或[mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html)服务器收到大于[max\_allowed\_packet](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html#sysvar_max_allowed_packet)字节的数据包时，它会发出[ER\_NET\_PACKET\_TOO\_LARGE](https://dev.mysql.com/doc/mysql-errors/8.0/en/server-error-reference.html#error_er_net_packet_too_large)错误（可在`exception.log`中看到）并关闭连接。 对于某些客户端，如果通信数据包太大，则在查询&#x200B;*错误期间您还可能会收到[!DNL MySQL]与*&#x200B;服务器的丢失连接。

<u>重现步骤</u>

各种任务都可能导致此问题。 这可能包括尝试将大量产品导入Adobe Commerce或发送过多数据的事务性查询。 结果是`var/log/exception.log`中的数据库连接错误和其他问题，如未成功导入产品。

## 原因

[!DNL MySQL] `max_allowed_packets`设置的默认值16MB不够大，无法满足您的需求。

## 解决方案

1. 标识单个行超过当前`max_allowed_packet`限制的查询。 需要重写此类查询以减少返回的数据量。 可以通过在`SELECT`语句中具有更少列数或为表设计中的各个列选择更小的数据类型来实现这一点。 如果您拥有New Relic帐户，请使用[New Relic APM错误页面](https://docs.newrelic.com/docs/apm/apm-ui-pages/error-analytics/errors-page-explore-events-behind-errors)、[New Relic APM数据库页面](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time)和[New Relic日志](https://docs.newrelic.com/docs/logs/log-management/get-started/get-started-log-management)搜索相关查询。
1. 为快速修正，您可以在`max_allowed_packet`提交票证[时临时请求增加](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)的大小，但这由客户工程团队自行决定，因为值过大可能会导致网络拥塞，进而导致复制失败。
1. 作为最佳实践，您应在CLI中针对某些大型数据库表运行以下命令：

   ```
   show table status like [table name to match]
   ```

   评估在这些表上运行的查询，以确定是否超过建议的`max_allowed_packet`大小(16MB)。 执行步骤一中的相同过程，减少此类查询返回的数据。

## 相关阅读

* 我们的开发人员文档中的[内部部署安装概述](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview)。
* 在我们的支持知识库中[云基础架构上Adobe Commerce的数据库最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)。
* [解决支持知识库中数据库性能问题的最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)。
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
