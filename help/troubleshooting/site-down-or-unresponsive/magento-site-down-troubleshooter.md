---
title: Adobe Commerce站点故障排查器
description: 单击每个问题以显示故障诊断程序每个步骤中的答案详细信息。
exl-id: 10a2313e-cc82-4ffc-9247-624884f3e165
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Adobe Commerce站点故障排查器

单击每个问题以显示故障诊断程序每个步骤中的答案详细信息。

## 步骤1 {#step-1}

+++**<https://status.adobe.com>是否显示任何问题？**

a.是 — 如果您检查[AdobeMagento状态](https://status.adobe.com/products/3350)并显示问题，请打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以进行进一步调查。\
b.否 — 如果您检查了[AdobeMagento状态](https://status.adobe.com/products/3350)并且它没有显示问题，请继续执行[步骤2](#step-2)。

+++

## 步骤2 {#step-2}

+++**http://status.fastly.com是否显示任何问题？**

a.是 — 如果您检查[Fastly状态](https://status.fastly.com/)并显示问题，请打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以进行进一步调查。\
b.否 — 如果您检查[Fastly状态](https://status.fastly.com/)并且它未显示问题，请继续执行[步骤3](#step-3)。

+++

## 步骤3 {#step-3}

+++**在Web浏览器中查看您的网站。 你收到200 (OK)代码吗？**

要在&#x200B;**Firefox**&#x200B;中检查错误代码：单击&#x200B;**打开菜单**&#x200B;图标> **Web开发人员** > **切换工具** > **网络**&#x200B;选项卡> **所有**&#x200B;筛选器> **状态**&#x200B;列。 要在&#x200B;**Chrome**&#x200B;中检查错误代码：单击&#x200B;**打开菜单**&#x200B;图标> **更多工具** > **开发人员工具** > **网络**&#x200B;选项卡> **所有**&#x200B;筛选器> **状态**&#x200B;列。

a.是 — 打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以进行进一步调查。\
b.否 — 继续执行[步骤4](#step-4)。

+++

## 步骤4 {#step-4}

+++**您收到了哪个网站错误代码？**

a.错误代码500 — 检查`/var/log/platform/`的日志。 如果此数据不会向您显示问题，您可以打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，并包含您目前掌握的疑难解答信息以供进一步调查。

b.错误代码503 — 检查`var/reports`的日志。 如果此数据不会向您显示问题，您可以打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，并包含您目前掌握的疑难解答信息以供进一步调查。

c.错误代码404 — 运行以下查询： `SELECT f.flag_data->>'$.current_version' as flag_version, (su.id IS NOT NULL) as update_exists FROM flag f LEFT JOIN staging_update su ON su.id = f.flag_data->>'$.current_version' WHERE flag_code = 'staging';`如果查询返回一个表，其中`update_exists`值为“0”，由于内容暂存问题，请参阅storefront和Admin的所有页面上的[错误404](/help/troubleshooting/site-down-or-unresponsive/error-404-on-all-pages-due-to-content-staging-issue.md)文章。 在所有其他情况下，请继续执行[步骤5](#step-5)。

d.其他错误代码 — 继续执行[步骤5](#step-5)。

+++

## 步骤5 {#step-5}

+++**您的网站速度是否太慢，或者在MySQL或Redis中服务器负载过高、CPU负载过高、请求处理速度缓慢，或者发生中断？**

a.是 — 继续执行[从CLI](/help/troubleshooting/miscellaneous/checking-for-ddos-attack-from-cli.md)检查DDOS攻击的步骤。\
b.否 — 检查`/var/log/exception.log`和`/var/log/deploy.log`的日志，如果此数据不向您显示问题，请继续执行[步骤6](#step-6)。

+++

## 步骤6 {#step-6}

+++**您是否有部署错误或部署失败？**

a.是 — 继续执行[步骤13](#step-13)。\
b.否 — 继续执行[步骤7](#step-7)。

+++

## 步骤7 {#step-7}

+++**您有Elasticsearch错误吗？**

a.是 — 继续执行[检查Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)的步骤。\
b.否 — 继续执行[步骤8](#step-8)。

+++

## 步骤8 {#step-8}

+++**您的MySQL数据库是否有较慢的查询或不正确的查询？**

a.是 — 继续[在MySQL](/help/troubleshooting/database/checking-slow-queries-and-processes-mysql.md)中检查慢速查询和进程花费太长时间，并在此[MySQL查询教程](https://dev.mysql.com/doc/refman/5.5/en/entering-queries.html)中检查您的查询结构。\
b.否 — 继续执行[步骤9](#step-9)。

+++

## 步骤9 {#step-9}

+++**您的静态内容是否不可用？**

a.是 — 继续查阅[检查静态内容](https://support.magento.com/hc/en-us/articles/360031624091)文章。\
b.否 — 继续执行[步骤10](#step-10)。

+++

## 步骤10 {#step-10}

+++**是否在日志中看到PHP致命错误？**

a.是 — 继续咨询[常见PHP致命错误和解决方案](/help/troubleshooting/miscellaneous/common-php-fatal-errors-and-solutions.md)。\
b.否 — 继续执行[步骤11](#step-11)。

+++

## 步骤11 {#step-11}

+++**您是否看到Redis错误？**

a.是 — 继续执行步骤，以验证Redis是否正在运行](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)以及[Redis疑难解答](https://redis.io/topics/problems)。[\
b.否 — 继续执行[步骤12](#step-12)。

+++

## 步骤12 {#step-12}

+++**您是否看到索引器错误？**

a.是 — 如果索引被其他进程锁定，请查阅[索引被其他进程](/help/troubleshooting/miscellaneous/index-is-locked-by-another-process.md)锁定。 如果您有其他索引器错误，请打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以便进一步调查。\
b.否 — 打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以进行进一步调查。

+++

## 步骤13 {#step-13}

+++**您的自定义模块是否存在问题？**

a.是 — 继续查阅[常规自定义模块疑难解答帮助](/help/troubleshooting/miscellaneous/general-custom-module-troubleshooting-help.md)。\
b.否 — 继续执行[步骤14](#step-14)。

+++

## 步骤14 {#step-14}

+++**您是否具有挂接后故障？**

a.是 — 继续在此[MySQL服务器错误消息引用](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html)中检查您的MySQL错误。\
b.否 — 继续执行[步骤15](#step-15)。

+++

## 步骤15 {#step-15}

+++**您是否遇到编辑器修补程序问题？**

a.是 — 继续咨询[应用修补程序将导致您的网站关闭](/help/troubleshooting/site-down-or-unresponsive/applying-a-patch-takes-your-site-down.md)。\
b.否 — 继续执行[步骤16](#step-16)。

+++

## 步骤16 {#step-16}

+++**是否存在SQL数据库错误？**

a.是 — 继续在此[MySQL服务器错误消息引用](https://dev.mysql.com/doc/mysql-errors/5.7/en/server-error-reference.html)中检查您的MySQL错误。\
b.否 — 继续执行[步骤17](#step-17)。

+++

## 步骤17 {#step-17}

+++**您有MySQL数据库死锁还是没有响应的MySQL数据库？**

a.是 — 继续检查MySQL](/help/troubleshooting/database/deadlocks-in-mysql.md)文章中此[死锁中的MySQL死锁。\
b.否 — 打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以进行进一步调查。

+++

[返回步骤1](#step-1)

单击[此处](/help/troubleshooting/site-down-or-unresponsive/site-down-troubleshooting-diagram.md)查看站点关闭疑难解答流程图。
