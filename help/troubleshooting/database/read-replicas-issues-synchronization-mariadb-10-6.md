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

此 `slave_parallel_mode` 默认情况下，数据库上的config已更改为 *优化* 值应为 *保守*，和 `synchronous_replication` ece-Tools中的值默认为 *true* 值应为 *false*.

## 解决方案

1. 检查 `slave_parallel_mode` 参数设置为 *保守* (您将需要 [提出支持票证](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket) 如果值未显示为 *保守*)。 要检查，请运行以下命令：

   ```
    MariaDB [main]> show variables like 'slave_parallel_mode';
    +---------------------+--------------+
    | Variable_name       | Value        |
    +---------------------+--------------+
    | slave_parallel_mode | conservative |
    +---------------------+--------------+
    1 row in set (0.001 sec)
   ```

1. 更新 `.magento.env.yaml` 数据库配置用于：

   ```yaml
       DATABASE_CONFIGURATION:
        _merge: true
           slave_connection:
               default:
                   synchronous_replication: false
   ```



有关更新数据库配置的步骤，请参阅 [DATABASE_CONFIGURATION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#database_configuration) 《Commerce on Cloud Infrastructure指南》的部署变量主题中。


## 相关阅读

* [配置环境变量以进行部署](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html) 《Commerce on Cloud Infrastructure指南》中的。
* [数据库配置的最佳实践](/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html) 实施行动手册中的。
