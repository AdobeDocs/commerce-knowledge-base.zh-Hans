---
title: 在云基础架构上的Adobe Commerce上创建数据库转储
description: 本文讨论在云基础架构上的Adobe Commerce上创建数据库(DB)转储的可能性（和推荐的方法）。
exl-id: 4a2e54ac-8d65-4e51-8337-08f9748dc6c0
feature: Cloud
source-git-commit: 0948b2a94ee4f2a355e7c024a09929f0ad223783
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 在云基础架构上的Adobe Commerce上创建数据库转储

本文讨论在云基础架构上的Adobe Commerce上创建数据库(DB)转储的可能性（和推荐的方法）。

您只需要使用一个变体（选项）来转储数据库。 这些选项适用于任何环境类型（集成、暂存、生产）和任何计划(云基础架构上的Adobe Commerce入门计划架构和云基础架构上的Adobe Commerce Pro计划架构)。

## 前提条件：通过SSH连接到环境

要使用本文中讨论的任何变体在Adobe Commerce上转储您的数据库，您必须先[SSH到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans)。

>[!WARNING]
>
>无论您是选择选项1还是选项2，都要在非高峰时间对数据库辅助节点运行该命令。

## 选项1：db-dump （**ece-tools；建议**）

您可以使用[ECE-Tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=zh-Hans)命令转储数据库：

```php
vendor/bin/ece-tools db-dump
```

这是推荐且最安全的选项。

请参阅我们的Commerce on Cloud Infrastructure指南中的[转储您的数据库(ECE-Tools)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/database-dump.html?lang=zh-Hans)。

## 选项2：mysqldump

>[!WARNING]
>
>不要对数据库群集运行此命令。 群集不会区分它是针对主数据库还是辅助数据库运行的。 如果群集针对主数据库运行此命令，则数据库将无法执行写操作，直到转储完成，并且可能会影响性能和站点稳定性。

您可以使用本机MySQL `mysqldump`命令转储数据库。

整个命令可能如下所示：

```sql
mysqldump -h <host> -u <username> -p <password> --single-transaction <db_name> | gzip > /tmp/<dump_name>.sql.gz
```

通过运行`mysqldump`命令创建并保存在`\tmp`中的数据库备份应从此位置移动。 它不应占用`\tmp`中的存储空间（这可能会导致问题）。

要获取数据库凭据（主机、用户名和密码），可以调用`MAGENTO_CLOUD_RELATIONSHIPS`环境变量：

```
echo $MAGENTO_CLOUD_RELATIONSHIPS |base64 --d |json_pp
```

**相关文档：**

* [mysqldump — 官方的MySQL文档中的数据库备份程序](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)。
* 我们的Commerce on Cloud Infrastructure指南中的[特定于云的变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=zh-Hans)（请参阅`MAGENTO_CLOUD_RELATIONSHIPS`）。
