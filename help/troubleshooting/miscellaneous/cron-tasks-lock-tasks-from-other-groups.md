---
title: “[!DNL Cron]任务锁定来自其他组的任务”
description: 本文为Adobe Commerce提供了与阻止其他 [!DNL cron] 作业的某些长期的 [!DNL cron] 作业相关的云基础架构问题的解决方案。
exl-id: b5b9e8b3-373c-4f93-af9c-85da84dbc928
feature: Configuration
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# [!DNL Cron]任务从其他组锁定任务

本文为Adobe Commerce提供了一个解决云基础架构问题的解决方案，该问题与阻止其他[!DNL cron]作业的某些长期[!DNL cron]作业相关。

## 受影响的产品和版本

* Adobe Commerce on cloud infrastructure Pro计划架构
* 2019年5月之前入门

## 问题

在Adobe Commerce for cloud上，当您具有复杂的[!DNL cron]任务（长期任务）时，它们可能会锁定其他任务以供执行。 例如，索引器的任务重新索引失效的索引器。 它可能需要几个小时才能完成，并且会锁定其他默认[!DNL cron]作业，例如发送电子邮件、生成站点地图、客户通知和其他自定义任务。

<u>症状</u>：

未执行[!DNL cron]作业执行的进程。 例如，产品更新不适用于小时，或者客户报告未收到电子邮件。

打开`cron_schedule`数据库表时，您会看到状态为`missed`的作业。

## 原因

以前，在我们的云环境中，Jenkins服务器用于运行[!DNL cron]作业。 Jenkins一次只能运行一个作业实例；因此，一次只能运行一个`bin/magento cron:run`进程。

## 解决方案

1. 联系[Adobe Commerce支持](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以启用自托管[!DNL crons]。
1. 编辑[!DNL Git]分支中Adobe Commerce代码的根目录中的`.magento.app.yaml`文件。 添加以下内容：

   ```yaml
     crons:
     cronrun:
     spec: "* * * * *"
     cmd: "php bin/magento cron:run"
   ```

1. 保存文件并将更新推送到暂存环境和生产环境（与对集成环境执行此操作的方式相同）。

>[!NOTE]
>
>无需将存在多个`cron:run`的旧[!DNL cron]配置传输到新[!DNL cron]计划；如上所述添加的常规`cron:run`任务已经足够。 但是，如果您有任何自定义作业，则需要转移这些作业。

### 检查您是否启用了自管理[!DNL cron]（仅用于Cloud Pro暂存和生产环境）

要检查自管理[!DNL cron]是否已启用，请运行`crontab -l`命令并观察结果：

* 如果您能够看到类似以下的任务，则启用自托管[!DNL cron]：

  ```bash
  username@hostname:~$ crontab -l    # Crontab is managed by the system, attempts to edit it directly will fail.
  SHELL=/etc/platform/username/cron-run    MAILTO=""    # m h dom mon dow job_name    * * * * * cronrun
  ```

* 如果您无法看到任务并收到&#x200B;*“不允许使用此程序”*&#x200B;错误消息，则未启用自托管[!DNL cron]。

>[!NOTE]
>
>上述检查是否已启用自管理[!DNL cron]的命令不适用于入门计划和开发/集成环境。

## 相关阅读

* 在我们的开发人员文档中[设置 [!DNL cron] 作业](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
