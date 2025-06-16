---
title: 适用于Adobe Commerce的高级报表疑难解答程序
description: 使用此故障诊断程序工具可解决Adobe Commerce上的高级报表问题。 这包括高级报告未显示任何数据和404错误。 单击每个问题以显示故障诊断程序每个步骤的答案。
exl-id: 7ef9870c-b6b6-4144-a5a7-81aa20a1606c
feature: Cache, Support
role: Developer
source-git-commit: 842c329b5d8bacf72ac689412fde5a5d76d16e85
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 0%

---

# 适用于Adobe Commerce的高级报表疑难解答程序

使用此故障诊断程序工具可解决Adobe Commerce上的高级报表问题。 这包括高级报告未显示任何数据和404错误。 单击每个问题以显示故障诊断程序每个步骤的答案。

## 第1步 — 确认站点符合高级报告要求 {#step-1}

+++**您的网站是否符合高级报告要求？**

使用高级报告时，出现“404错误”页面。 您的网站是否符合[高级报告要求](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)？

a.是 — 继续执行[步骤2](#step-2)。\
b.否 — 按照[高级报告要求](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#requirements)中的步骤完成网站的高级报告要求。 然后，继续执行[步骤2](#step-2)。

+++

## 第2步 — 是否存在使用多种基础货币的订单？ {#step-2}

+++**是否使用了多个基础货币？**

是否使用了多个基本货币（在订单和配置中）？ 运行此[!DNL SQL]命令以获取当前配置： `SELECT value FROM core_config_data WHERE path = 'currency/options/base';` 。

a.是 — 如果查询返回了多行，则不能使用“高级报告”，因为我们仅支持一种货币。\
b.否 — 输出仅显示一种货币。 示例： `USD`。 是否曾经使用过多个基础货币（按订单）？ 运行此[!DNL SQL]命令以获取历史订单数据：\
`SELECT DISTINCT base_currency_code FROM sales_order;`。
**注意：此命令要求进行完整的表扫描，因此对于记录数量多的表，当查询正在执行**&#x200B;以获取历史订单数据时，这可能会对性能产生影响。
如果曾经使用过多种基础货币，则不能使用高级报告，因为我们只支持一种货币。 如果输出只显示一种货币，请执行[步骤3](#step-3)。

+++

## 步骤3 — 检查是否正在使用拆分数据库 {#step-3}

+++**您是否使用拆分数据库解决方案？**

您是否使用[拆分数据库解决方案](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/storage/split-db/multi-master)？

a.是 — 对拆分数据库解决方案和清除缓存使用高级报告404错误中的修补程序&#x200B;**MDVA-26831**。 请等待24小时以使作业再次运行，然后重试。\
b.否 — 继续执行[步骤4](#step-4)。

+++

## 步骤4 — 确认启用高级报告 {#step-4}

+++**是否启用了高级报告？**

检查&#x200B;**管理员** > **商店** > **设置** > **配置** > **常规** > **高级报告**。 有关详细步骤，请查看[高级报告：启用高级报告](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)。

a.是 — 继续执行[步骤5](#step-5)。\
b.否 — [启用高级报告](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)并保存，等待24小时让Adobe Commerce和高级报告同步。 检查您的数据现在是否加载。 如果它确实解决了这个问题。 如果未执行[步骤5](#step-5)。

+++

## 步骤5 — 检查令牌 {#step-5}

+++**是否有令牌？**

通过运行以下查询检查是否存在令牌： `SELECT * FROM core_config_data WHERE path LIKE 'analytics/general/token' \G`是否存在令牌？

a.是 — 继续执行[步骤7](#step-7)。\
b.否 — 如果令牌值为NULL或数据库中没有记录，请继续执行[步骤6](#step-6)。

+++

## 步骤6 — 使用行 {#step-6}

+++**查询是否返回行？**

通过运行此查询检查标志表中的计数器值： ``SELECT * FROM `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter'\G``查询是否返回行？

a.是 — 执行以下步骤：1. 运行以下查询：\
``DELETE from `flag` where `flag_code` = 'analytics_link_subscription_update_reverse_counter';``\
2\。 [在设置中禁用并启用高级报告模块](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)，并[重新授权令牌](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active)。\
3\。 等待24小时，以便Adobe Commerce和高级报表进行同步。 如果仍无法在高级报表中看到数据，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 如果查询未返回任何内容，请执行以下步骤：1. [在设置中禁用并启用高级报告模块](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#step-1-enable-advanced-reporting)，并[重新授权令牌](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting#verify-that-the-integration-is-active)。\
2\。 等待24小时，以便Adobe Commerce和高级报表进行同步。 如果仍无法在高级报表中看到数据，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

## 步骤7 — 检查`cron_schedule`表中的记录 {#step-7}

+++**`cron_schedule`表中是否有记录？**

检查作业`analytics_collect_data`是否通过运行此查询而执行： `SELECT * FROM cron_schedule WHERE job_code LIKE 'analytics_collect_data' \G`

a.是 — 如果有记录，且&#x200B;**status**&#x200B;列显示&#x200B;_missed_，则使用此KB文章“更新高级报告”中的修补程序在自己的cron组上运行。\
b.是 — 如果有记录，且&#x200B;**状态**&#x200B;列显示&#x200B;_成功_，请继续执行[步骤9](#step-9)。\
c.是 — 如果有记录，且&#x200B;**状态**&#x200B;列显示&#x200B;_错误_，请继续执行[步骤8。](#step-8)\
d.否 — 如果没有记录，请继续执行[步骤8](#step-8)。

+++

## 步骤8 — 检查`support_report.log`中的作业 {#step-8}

+++**作业是否已登录`support_report.log`？**

运行命令： `zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz | tail`

a.是 — 如果查询的输出指示作业成功，例如`Cron Job analytics_collect_data is successfully finished`，则继续执行[步骤9](#step-9)。\
b.否 — 如果日志中没有记录，则[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
c.是 — 如果有记录但出现错误，请继续执行[步骤10](#step-10)。

+++

## 步骤9 — 检查`data.tgz`文件 {#step-9}

+++**系统中是否存在文件`data.tgz`，访问日志中是否有记录？**

要检查文件`data.tgz`是否存在，请运行此命令 — 它应返回具有哈希名称的目录：

```
ls -ltr pub/media/analytics/
```

要检查access.logs中是否存在记录，请运行此命令：

* 在Commerce Cloud上：

  ```
  {{zgrep -i analytics /var/log/platform/*/access.log* | grep MagentoBI}}
  ```

* 对于内部部署，请相应地替换文件路径：
  `zgrep -i analytics <your web server's log path>/access.log* | grep MagentoBI`

a.是 — 如果文件`data.tgz`存在并且访问日志中有记录，但您仍然存在404错误，则您需要[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。\
b.否 — 继续执行[步骤10](#step-10)。

+++

## 步骤10 — 检查错误消息 {#step-10}

+++**cron作业是否引发错误消息？**

示例：在`cron_schedule`表中看到错误&#x200B;*“/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0文件无法删除*。 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0？lang=en)：没有此类文件或目录*

a.是 — 在[中使用ACSD-50165修补程序无法删除该文件。 警告！unlink：管理员](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-26887)中没有此类文件或目录错误，请等待24小时以使作业再次运行，然后重试。\
b.否 — 继续执行[步骤11](#step-11)。

+++

## 步骤11 — 验证是否存在页面生成器错误 {#step-11}

+++**页面生成器是否导致错误？**

示例： `report.ERROR: Cron Job analytics_collect_data has an error: substr_count() expects parameter 1 to be string, null given. Statistics: {"sum":0,"count":1,"realmem":0,"emalloc":0,"realmem_start":224919552,"emalloc_start":216398384} [] []`

a.是 — 在Adobe Commerce上的常见高级报告cron作业错误中使用MDVA-19391修补程序，等待24小时以使作业再次运行并重试。\
b.否 — [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

+++

[返回步骤1](#step-1)

## 相关阅读

[在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
