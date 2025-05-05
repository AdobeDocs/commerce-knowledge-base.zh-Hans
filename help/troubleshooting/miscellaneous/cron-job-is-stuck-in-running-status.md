---
title: “[!DNL Cron]作业卡在**正在运行**状态”
description: 本文提供了当Adobe Commerce [!DNL cron] 作业未完成执行并持续处于“正在运行”状态时（阻止其他 [!DNL cron] 作业运行）的解决方案。 发生这种情况的原因有很多，例如网络问题、应用程序崩溃和重新部署问题。
exl-id: 11e01a2b-2fcf-48c2-871c-08f29cd76250
feature: Configuration
role: Developer
source-git-commit: 08a241131453725a86eda5f267a209e6705da2e3
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Cron]作业卡在“正在运行”状态

本文针对Adobe Commerce [!DNL cron]作业未完成执行并持续处于“正在运行”状态时提供了解决方案，该状态会阻止其他[!DNL cron]作业运行。 发生这种情况的原因有很多，例如网络问题、应用程序崩溃和重新部署问题。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，所有版本

## 症状 {#symptom}

必须重置的[!DNL cron]作业的症状包括：

* `cron_schedule`队列中出现大量作业
* 网站性能开始降低
* 作业无法按计划执行

## 解决方案 {#solutions}

### 用于同时停止所有[!DNL cron]作业的解决方案 {#solution-stop-all-crons-at-once}

>[!WARNING]
>
>运行此命令而不使用`--job-code`选项会重置&#x200B;*所有* [!DNL cron]作业（包括当前正在运行的作业），因此我们建议仅在例外情况下使用它，例如，在您验证必须重置所有[!DNL cron]作业之后。 默认情况下，重新部署将运行此命令以重置[!DNL cron]个作业，以便在环境备份后正确恢复它们。 避免在索引器运行时使用此解决方案。

要解决此问题，必须使用`cron:unlock`命令重置[!DNL cron]作业。 此命令更改数据库中[!DNL cron]作业的状态，强制结束该作业以允许其他计划的作业继续执行。

1. 打开终端并使用[SSH密钥](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/secure-connections)连接到受影响的环境。
1. 获取MySQL数据库凭据：    ```shell    echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp    ```
1. 使用`mysql`连接到数据库：    ```shell    mysql -hdatabase.internal -uuser -ppassword main    ```
1. 选择`main`数据库：    ```shell    use main    ```
1. 查找所有正在运行的[!DNL cron]作业：    ```shell    SELECT * FROM cron_schedule WHERE status = 'running';    ```
1. 复制运行时间超过正常时间的任何作业的`job_code`。
1. 使用上一步中的计划ID解锁特定[!DNL cron]作业：    ```shell    ./vendor/bin/ece-tools cron:unlock --job-code=<job_code_1> [... --job-code=<job_code_x>]    ```

### 用于停止单个[!DNL cron]的解决方案 {#solution-stop-a-single-cron}

1. 打开终端并使用[SSH密钥](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/secure-connections)连接到受影响的环境。
1. 使用以下命令检查长时间运行的任务：

   ```date; ps aux | grep '[%]CPU\|cron\|magento\|queue' | grep -v 'grep\|cron -f'```

1. 在输出中，如下面的示例输出中，您将看到当前日期和进程列表。 `START`列显示进程的开始时间或日期：

   ```
   Wed May  8 22:41:31 UTC 2019
   USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
   root       590  0.0  0.0  27528  2768 ?        Ss   Jan15   0:49 /usr/sbin/cron -f
   bxc2qly+ 25855  0.0  0.0  23724  2184 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe_stg-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe_stg-bxc2qlykqhbqe_stg
   bxc2qly+ 25860 57.7  1.3 584220 222692 ?       S    20:51   0:02 php bin/magento cron:run
   bxc2qly+ 25863  0.0  0.0  23724  2472 ?        S    20:51   0:00 logger -d -u /run/bxc2qlykqhbqe-cron.sock -p cron.info -s -t cron-bxc2qlykqhbqe-bxc2qlykqhbqe
   bxc2qly+ 25876 53.0  0.6 475472 111468 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25878 57.0  0.6 475472 112080 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25880 50.5  0.6 475472 111312 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25882 48.5  0.6 475472 111220 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25884 50.5  0.6 475472 111372 ?       R    20:51   0:01 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe_stg/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25890 32.5  0.6 475368 110672 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=staging --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25892 34.5  0.6 475472 110724 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=catalog_event --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25894 31.5  0.6 475368 110136 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=consumers --bootstrap=standaloneProcessStarted=1
   bxc2qly+ 25896 29.0  0.6 475320 109876 ?       R    20:51   0:00 /usr/bin/php7.1-zts /app/bxc2qlykqhbqe/bin/magento cron:run --group=ddg_automation --bootstrap=standaloneProcessStarted=1
   ```

1. 如果您看到长时间运行的[!DNL cron]作业可能属于块部署进程，则可以使用`kill`命令终止该进程。 您可以识别&#x200B;**进程ID**（找到`PID`列），然后将`PID`放入命令中以终止该进程。
**终止进程**&#x200B;命令为：

   ```kill -9 <PID>```

1. 如果您尝试重新部署，则可以重新部署。
