---
title: 从暂存或生产环境恢复数据库快照
description: 本文说明如何在云基础架构上从Adobe Commerce上的暂存或生产环境恢复数据库快照。
exl-id: 1026a1c9-0ca0-4823-8c07-ec4ff532606a
source-git-commit: b99d78845128ca3d995cbbb5df0799449ca954e3
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 从恢复数据库快照 [!DNL Staging] 或 [!DNL Production]

本文说明如何还原数据库 [!DNL snapshot] 从 [!DNL Staging] 或 [!DNL Production] 在Adobe Commerce on Cloud Pro基础架构上。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce， [所有受支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

选择最适合您的具体情况：

* [方法1：传输数据库 [!DNL dump] 导入到本地计算机](#meth2).
* [方法2：导入数据库 [!DNL dump] 直接从服务器](#meth3).

## 方法1：传输数据库 [!DNL dump] 导入到本地计算机 {#meth2}

步骤如下：

1. 使用 [!DNL SFTP]，导航到数据库的位置 [!DNL snapshot] 放置，通常位于您的第一个服务器/节点上 [!DNL cluster] (例如： `/mnt/recovery-<recovery_id>`)。 注意：如果您的项目基于Azure，即，您的项目URL类似于https://us-a1.magento.cloud/projects/&lt;cluster_id>，则快照将放在 `/mnt/shared/<cluster ID>/all-databases.sql.gz` 或 `/mnt/shared/<cluster ID_stg>/all-databases.sql.gz` 而是。

   注意：Azure项目上的快照格式将不同，并包含无法导入的其他数据库。 在导入快照之前，您必须先执行其他步骤来提取相应的数据库，然后再导入转储。

   对于生产：

   ```sql
   cd /mnt/shared/<cluster ID/
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

   对于暂存：

   ```sql
   cd /mnt/shared/<cluster ID/ | cd /mnt/shared/<cluster ID_stg>
   gunzip all-databases.sql.gz 
   head -n 17 all-databases.sql > <cluster ID_stg>.sql
   sed -n '/^-- Current Database: `wyf2o4zlrljjs`/,/^-- Current Database: `/p' all-databases.sql >> <cluster ID_stg>.sql 
   gzip <cluster ID_stg>.sql  
   zcat <cluster ID_stg>.sql.gz | \
   sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | \
   mysql -h 127.0.0.1 \
   -u $DB_USER \
   --password=$MYSQL_PWD $DB_NAME \
   --init-command="SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT ;SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS ;SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION ;SET NAMES utf8 ;SET @OLD_TIME_ZONE=@@TIME_ZONE ;SET TIME_ZONE='+00:00' ;SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 ;SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 ;SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' ;SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0;"
   ```

1. 复制数据库 [!DNL dump file] (例如： `<cluster ID>.sql.gz` 对象 [!DNL Production] 或 `<cluster ID_stg>.sql.gz` 对象 [!DNL Staging])到本地计算机。
1. 确保您已设置 [!DNL SSH tunnel] 要远程连接到数据库，请执行以下操作： [[!DNL SSH] 和 [!DNL sFTP]： [!DNL SSH tunneling]](https://devdocs.magento.com/cloud/env/environments-ssh.html#env-start-tunn) 在我们的开发人员文档中。
1. 连接到数据库。

   ```sql
   mysql -h <db-host> -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] 数据库；位于 [!DNL MariaDB] 提示，输入：

   (用于 [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (用于 [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 输入以下命令以导入 [!DNL snapshot]：

   (用于 [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

   (用于 [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -P <db-port> -p -u   <db-user> <db-name>
   ```

## 方法2：导入数据库 [!DNL dump] 直接从服务器 {#meth3}

步骤如下：

1. 导航到数据库的位置 [!DNL snapshot] 放置，通常位于您的第一个服务器/节点上 [!DNL cluster] (例如： `/mnt/recovery-<recovery_id>`)。
1. 至 [!DNL drop] 并重新创建云数据库，首先连接到数据库：

   ```sql
   mysql -h 127.0.0.1 -P <db-port> -p -u <db-user> <db-name>
   ```

1. [!DNL Drop] 数据库；位于 [!DNL MariaDB] 提示，输入：

   (用于 [!DNL Production])

   ```sql
   drop database <cluster ID>;
   ```

   (用于 [!DNL Staging])

   ```sql
   drop database <cluster ID_stg>;
   ```

1. 输入以下命令以导入 [!DNL snapshot]：

   (用于从导入数据库备份 [!DNL Production])

   ```sql
   zcat <cluster ID>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   (用于从导入数据库备份 [!DNL Staging])

   ```sql
   zcat <cluster ID_stg>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   （用于从任何其他环境导入数据库备份）

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

   （用于从任何其他环境导入数据库备份）

   ```sql
   zcat <database-backup-name>.sql.gz | sed -e 's/DEFINER[ ]*=[ ]*[^*]*\*/\*/' | mysql -h 127.0.0.1 -p -u <db-user> <db-name>
   ```

## 相关阅读

在我们的开发人员文档中：

* [导入代码：导入数据库](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html#cloud-import-db)
* [[!DNL Snapshots] 和 [!DNL backup] 管理： [!DNL Dump] 您的数据库](https://devdocs.magento.com/cloud/project/project-webint-snap.html#db-dump)
