---
title: 带有MariaDB 10.6的Adobe Commerce Cloud 2.4.6上的只读副本问题
description: 本文介绍了如何使用MariaDB 10.6对Adobe Commerce Cloud 2.4.6上的只读副本问题进行故障诊断。
feature: Configuration
role: Developer,Admin
exl-id: b7af1cc3-93ff-40c5-8959-076cedddb56d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# 带有MariaDB 10.6的Adobe Commerce Cloud 2.4.6上的只读副本问题

本文为在Adobe Commerce Cloud 2.4.6和MariaDB 10.6+上使用只读副本时出现意外行为提供了解决方案。

## 受影响的产品和版本

* MariaDB 10.6+
* 云基础架构上的Adobe Commerce 2.4.6

## 问题

非关键读取显示不正确的信息。

## 原因

当值应为&#x200B;*conservative*&#x200B;时，数据库上的`slave_parallel_mode`配置默认更改为&#x200B;*optimistics*，而Ece-Tools中的`synchronous_replication`值默认为&#x200B;*true*，而值应为&#x200B;*false*。

## 解决方案

1. 检查`slave_parallel_mode`参数是否设置为&#x200B;*conservative* （如果值未显示为&#x200B;*conservative*，则需要[引发支持票证](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)）。 要检查，请运行以下命令：

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. 将`.magento.env.yaml`数据库配置更新为：

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



有关更新数据库配置的步骤，请参阅Commerce on Cloud Infrastructure指南中“部署变量”主题中的[DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=zh-Hans#database_configuration)。


## 相关阅读

* 在《云基础架构上的Commerce指南》中[为部署](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)配置环境变量。
* 在《实施行动手册》中[数据库配置的最佳实践](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)。
