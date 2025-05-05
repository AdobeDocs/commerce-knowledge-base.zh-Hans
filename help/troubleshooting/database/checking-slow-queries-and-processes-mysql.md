---
title: 正在检查慢查询和进程MySQL
description: 本文讨论了一些MySQL常见问题（查询缓慢、流程耗时过长），这些问题可能会对商户的网站及其指示的解决方案产生不利影响。
exl-id: cae02e4f-d8cb-4074-abac-24ead22bdc07
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 正在检查慢查询和进程MySQL

本文讨论了一些MySQL常见问题（查询缓慢、流程耗时过长），这些问题可能会对商户的网站及其指示的解决方案产生不利影响。

## 正在检查MySQL“慢查询”

### 描述

如果由于数据库超载而导致中断，这些步骤将帮助您检查数据库的查询日志是否缓慢。

### 使用MySQL命令行分析查询(Adobe Commerce Cloud/内部部署/Magento Open Source)

1. 从命令行(云基础架构上的Adobe Commerce)登录到MySQL命令行(Adobe Commerce本地/Magento Open Source)或云服务器。
1. 检查慢查询日志中超过50秒的查询：

   ```bash
   grep 'Query_time: [5-9][0-9]\|Query_time: [0-9][0-9][0-9]' /var/log/mysql/mysql-slow.log -A 3
   ```

1. 转到<https://www.unixtimestamp.com/>（或类似的Unix时间戳转换器）并插入执行慢速查询的时间戳。
1. 如果时间与您经历的任何站点停机都相关，则可能是由于数据库过载所致。 检查数据库上当时有哪些加载。 此类载荷的示例包括：

* Cron进程
* 流量（机器人或人员）
* 导入/导出脚本
* 创建转储


### 使用[!DNL Percona Toolkit]分析查询(仅限Adobe Commerce Pro：云架构)

如果您的Adobe Commerce项目部署在Pro架构上，则可以使用[!DNL Percona Toolkit]来分析查询。

1. 对MySQL慢查询日志运行`pt-query-digest --type=slowlog`命令。
   * 要查找慢查询日志的位置，请参阅我们的开发人员文档中的&#x200B;**[[!UICONTROL Log locations > Service Logs]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hans)**。
   * 请参阅[[!DNL Percona Toolkit] > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest)文档。
1. 根据发现的问题，采取措施修复查询，使其运行速度更快。

## 正在检查MySQL“进程列表”

### 描述

这将有助于识别MySQL服务器是否处于活动状态并且没有卡住的查询。

### 步骤

1. 从命令行(云基础架构上的Adobe Commerce)登录到MySQL命令行(Adobe Commerce本地/Magento Open Source)或云服务器。
1. 使用以下代码块登录MySQL。 这将自动执行登录过程。

   ```MySQL
   `export DB_NAME=$(grep [\']db[\'] -A 20 app/etc/env.php | grep dbname | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_HOST=$(grep [\']db[\'] -A 20 app/etc/env.php | grep host | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export DB_USER=$(grep [\']db[\'] -A 20 app/etc/env.php | grep username | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/['][,]//");    export MYSQL_PWD=$(grep [\']db[\'] -A 20 app/etc/env.php | grep password | head -n1 | sed "s/.*[=][>][ ]*[']//" | sed "s/[']$//" | sed "s/['][,]//");    mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;`
   ```

1. 如果返回错误或响应时间超过30秒，则应联系支持部门以检查MySQL服务器。
1. 查看示例输出。

1. 以下是一些输出示例：

   ```MySQL
   `$ mysql -h $MYSQL_HOST -u $DB_USER --password=$MYSQL_PWD $DB_NAME -U -A -e 'show processlist;'    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | Id        | User          | Host               | db            | Command | Time | State          | Info                                                                                                 | Progress |    +-----------+---------------+--------------------+---------------+---------+------+----------------+------------------------------------------------------------------------------------------------------+----------+    | 123456789 | abcdefghijklm | 192.168.7.10:12345 | abcdefghijklm | Query   |    0 | Writing to net | SELECT `magento_versionscms_hierarchy_node`.*, `page_table`.`title` AS `page_title`, `page_table`.`i |    0.000 |    | 123456788 | abcdefghijklm | 192.168.7.10:12344 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456777 | abcdefghijklm | 192.168.7.10:12333 | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |    | 123456666 | abcdefghijklm | 192.168.5.8:12222  | abcdefghijklm | Sleep   |    0 |                | NULL                                                                                                 |    0.000 |`
   ```

1. 检查“时间”列以查看任何大于1800秒的时间；这表示完成某个进程可能花费的时间过长。 在“状态”列中记录进程的状态。
1. 检查查询，如果发现这些查询在该时间段内不应运行，则可能将其终止。 可能需要长时间运行的查询。


## 相关阅读

* 在dev.mysql.com中[MySQL显示Processlist语法](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html)。
* dev.mysql.com中的[MySQL终止语法](https://dev.mysql.com/doc/refman/8.0/en/kill.html)。
* 在开发人员文档中[安全性、性能和数据处理](https://developer.adobe.com/commerce/php/best-practices/extensions/security/)。
* 在开发人员文档中[MySQL帮助](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql)。
