---
title: MySQL中的死锁
description: 本文讨论MySQL中的死锁，以便在导致站点关闭、数据库导入停滞或其他Adobe Commerce问题时帮助识别和解决死锁。
exl-id: 529d1c0b-77f3-4604-9878-e7ea2c9c3640
feature: Best Practices, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MySQL中的死锁

本文讨论MySQL中的死锁，以便在导致站点关闭、数据库导入停滞或其他Adobe Commerce问题时帮助识别和解决死锁。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x和2.3.x
* 云基础架构2.2.x和2.3.x上的Adobe Commerce

## 问题

当两个或多个事务相互保留并请求锁时，就会在MySQL中出现死锁。 存在的死锁并不总是指示问题，但通常是已发生的某个其他MySQL或Adobe Commerce问题的症状。

应用程序、部署或MySQL日志通常会提及&#x200B;*“死锁”*&#x200B;错误或错误&#x200B;*“尝试获取锁定时发现死锁；请尝试重新启动事务。”*

## 原因

死锁可能有多重原因，但最常见的情况是，在同时执行DML/DDL查询时执行任何交互（网站/进程/cron作业/其他用户/MySQL维护/MySQL导入）。

例如，最佳做法是首先使您的网站处于维护模式，以避免向数据库发出SQL请求，从而避免出现MySQL数据库导入停滞的情况，这可能会导致死锁和数据库导入停滞。

## 解决方案

1. 检查应用程序、部署或MySQL日志中是否有死锁错误：
   * [Adobe Commerce和Magento Open Source日志位置](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/enable-logging.html)
   * 云基础架构上的[Adobe Commerce日志位置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html)
1. 检查您的MySQL进程列表，了解如何使用命令`mysql -e 'show full processlist';`运行进程
1. 如果在云基础架构上的Adobe Commerce上，请检查MySQL从属是否启用。 请参阅本文： [部署变量(MYSQL\_USE\_SLAVE\_CONNECTION)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection)。
1. 根据所涉及的错误，解决方案可能会自行出现，或者您可能需要在需要打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)时提供有用的日志信息。

## 相关阅读

* [如何最小化并处理死锁](https://dev.mysql.com/doc/refman/5.7/en/innodb-deadlocks-handling.html)
* [索引器优化 — 索引器表切换](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/)
* [批量操作 — 使用邮件](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

>[!NOTE]
>
>我们知道，本文可能仍然包含行业标准的软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。
