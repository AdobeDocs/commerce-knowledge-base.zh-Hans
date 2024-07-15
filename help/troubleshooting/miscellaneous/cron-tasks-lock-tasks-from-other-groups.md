---
title: Cron任务从其他组锁定任务
description: 本文为Adobe Commerce提供了一个解决与某些阻止其他cron作业的长期运行cron作业相关的云基础架构问题的解决方案。
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: faa80e8233438fc15781341b3a9d5325269d6d20
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Cron任务从其他组锁定任务

本文为Adobe Commerce提供了一个解决与某些阻止其他cron作业的长期运行cron作业相关的云基础架构问题的解决方案。

## 受影响的产品和版本

* Adobe Commerce on cloud infrastructure Pro计划架构
* 2019年5月之前入门

## 问题

在Adobe Commerce for Cloud上，当您具有复杂的cron任务（长期任务）时，它们可能会锁定其他任务以供执行。 例如，索引器的任务重新索引失效的索引器。 它可能需要几个小时才能完成，并且会锁定其他默认cron作业，例如发送电子邮件、生成站点地图、客户通知和其他自定义任务。

<u>症状</u>：

cron作业执行的进程不会执行。 例如，产品更新不适用于小时，或者客户报告未收到电子邮件。

打开`cron_schedule`数据库表时，您会看到状态为`missed`的作业。

## 原因

以前，在我们的云环境中，使用Jenkins服务器来运行cron作业。 Jenkins一次只能运行一个作业实例；因此，一次只能运行一个`bin/magento cron:run`进程。

## 解决方案

1. 联系[Adobe Commerce支持](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以启用自托管cron。
1. 在Git分支中Adobe Commerce代码的根目录中编辑`.magento.app.yaml`文件。 添加以下内容：

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. 保存文件并将更新推送到暂存环境和生产环境（与对集成环境执行此操作的方式相同）。

>[!NOTE]
>
>无需将存在多个`cron:run`的旧cron配置传输到新cron计划；如上所述添加的常规`cron:run`任务就足够了。 但是，如果您有任何自定义作业，则需要转移这些作业。

### 检查您是否启用了自管理cron（仅用于Cloud Pro暂存和生产）

要检查是否已启用自托管cron，请运行`crontab -l`命令并观察结果：

* 如果您能够看到以下任务，则启用自管理cron：

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* 如果您无法看到任务并收到&#x200B;*“不允许您使用此程序”*&#x200B;错误消息，则不会启用自托管cron。

>[!NOTE]
>
>上述检查是否已启用自管理cron的命令不适用于入门计划和开发/集成环境。

## 相关阅读

* 在开发人员文档中[设置cron作业](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)。
