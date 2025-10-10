---
title: 从暂存或生产环境恢复数据库快照
description: 本文说明如何在云基础架构上从Adobe Commerce上的暂存或生产环境恢复数据库快照。
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: 62815213ce54f72d27812b9c2d7b3997f2e88897
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# 从[!DNL Staging]或[!DNL Production]还原数据库快照

本文说明如何在Cloud Pro基础架构上的Adobe Commerce上从[!DNL snapshot]或[!DNL Staging]还原DB [!DNL Production]。


>[!NOTE]
>
>这些方法将还原&#x200B;**完整快照**。
>>如果需要恢复快照&#x200B;**部分**（例如，仅恢复目录表，而保留顺序表不变），则必须咨询开发人员或DBA。


## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

选择最适合您的具体情况：

>[!NOTE]
>
> 如果要将快照导入集成环境，请注意数据库大小。 大型数据库可能会导致导入后的性能下降。 建议先将快照导入暂存或本地环境，以查看并减小其大小，然后再将其转移到集成。 此外，如果在导入后出现性能问题，请考虑在集成分支中禁用cron作业。 有关详细信息，请参阅Commerce on Cloud Infrastructure指南中的[集成环境](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/pro-architecture#integration-environment)。

* [方法1：将数据库 [!DNL dump] 传输到本地计算机并导入它](#meth2)。
* [方法2：直接从服务器 [!DNL dump] 导入数据库](#meth3)。

## 方法1：将数据库[!DNL dump]传输到本地计算机并将其导入 {#meth2}


>[!NOTE]
>
> **Azure项目**&#x200B;上快照的格式将不同，并且包含&#x200B;**无法导入**&#x200B;的其他数据库。\
> 在导入快照之前，必须先执行其他步骤以&#x200B;**提取相应的数据库**，然后才能继续转储导入。

步骤如下：

1. 使用[!DNL SFTP]，导航到数据库[!DNL snapshot]的放置位置，通常位于[!DNL cluster]的第一个服务器/节点上（例如： `/mnt/recovery-<recovery_id>`）。
   > 基于&#x200B;**Azure的项目：**\
   > 如果您的项目基于Azure（即，您的项目URL类似于`https://us-a1.magento.cloud/projects/<cluster_id>`），则快照将放在：
   > * `/mnt/shared/<cluster ID>/all-databases.sql.gz`
   > * `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz`

   **特定于Azure的提取步骤**

   用于生产环境的&#x200B;**：**

   ```bash
   cd /mnt/shared/<cluster ID>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID>.sql 
   sed -n '/^-- Current Database: `<cluster ID>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID>.sql gzip <cluster ID>.sql
   zcat <cluster ID>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

   用于暂存的&#x200B;**：**

   ```bash
   cd /mnt/shared/<cluster ID_stg>/
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `<cluster ID_stg>`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. 将数据库[!DNL dump file]（例如： `<cluster ID>.sql.gz`的[!DNL Production]或`<cluster ID_stg>.sql.gz`的[!DNL Staging]）复制到本地计算机。
1. 请确保您已将[!DNL SSH tunnel]设置为远程连接到我们的开发人员文档中的数据库： [[!DNL SSH] 和 [!DNL sFTP]： [!DNL SSH tunneling]](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#env-start-tunn)。
1. 连接到数据库。

   ```bash
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop]数据库；在[!DNL MariaDB]提示符下，输入：

   （对于[!DNL Production]）

   ```bash
   drop database <cluster ID>;
   ```

   （对于[!DNL Staging]）

   ```bash
   drop database <cluster ID_stg>;
   ```

1. 输入以下命令以导入[!DNL snapshot]：

   （对于[!DNL Production]）

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   （对于[!DNL Staging]）

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## 方法2：直接从服务器导入数据库[!DNL dump] {#meth3}

步骤如下：

1. 导航到数据库[!DNL snapshot]的放置位置，通常在[!DNL cluster]的第一个服务器/节点上（例如： `/mnt/recovery-<recovery_id>`）。
1. 要[!DNL drop]并重新创建云数据库，请先连接到该数据库：

   ```bash
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop]数据库；在[!DNL MariaDB]提示符下，输入：

   （对于[!DNL Production]）

   ```bash
   drop database <cluster ID>;
   ```

   （对于[!DNL Staging]）

   ```bash
   drop database <cluster ID_stg>;
   ```

1. 删除数据库后，重新创建数据库：

   ```bash
   create database [database_name];
   ```

1. 输入以下命令以导入[!DNL snapshot]：

   （用于从[!DNL Production]导入数据库备份）

   ```bash
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   （用于从[!DNL Staging]导入数据库备份）

   ```bash
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   （用于从任何其他环境导入数据库备份）

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   （用于从任何其他环境导入数据库备份）

   ```bash
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## 相关阅读

在我们的开发人员文档中：

* [导入代码：导入数据库](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)
* [[!DNL Snapshots] 和 [!DNL backup] 管理： [!DNL Dump] 您的数据库](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)
* 云上的[备份（快照）：常见问题解答](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/faq/backup-snapshot-on-cloud-faq)
