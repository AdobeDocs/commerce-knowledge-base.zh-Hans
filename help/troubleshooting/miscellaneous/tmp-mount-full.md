---
title: Adobe Commerce的/tmp mount full故障诊断
description: 本文提供了一个解决方案，用于解决“/tmp”装载已满、站点可能已关闭以及无法通过SSH连接到节点的问题。
exl-id: e72d0f99-0060-474b-bb1c-2851896e1e43
feature: Storage
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# Adobe Commerce的/tmp mount full故障诊断

本文提供了一个解决方案，用于解决`/tmp`装载已满、站点可能已关闭以及无法通过SSH连接到节点的问题。

## 受影响的产品和版本

* Adobe Commerce 2.3.0 - 2.3.6-p1， 2.4.0 - 2.4.2

## 问题

`/tmp`装载已满可能会导致一系列可能的症状，其中包括以下错误：

* *SQLSTATE[HY000]：常规错误： 3写入文件时出错*
* *错误代码： 28*
* *设备(28)上没有剩余空间*
* *error session_start()： failed：设备*&#x200B;上已无剩余空间
* *错误1 (HY000)：无法创建/写入文件“/tmp/*”
* *SQL错误： 3，SQLState： HY000*
* *常规错误： 1021磁盘已满(/tmp)*
* *无法通过SSH访问节点：*
  *bash：无法为here-document创建临时文件：设备没有剩余空间*
* *errno： 28“设备上没有剩余空间”*
* *mysqld：磁盘正在完全写入“/tmp”*
* *[错误] mysqld：磁盘已满(/tmp)*
* *SQLSTATE[HY000]：常规错误： 1无法创建/写入文件“/tmp/”*
* *SQLSTATE[HY000]：常规错误：打开文件“/tmp/”*&#x200B;时资源不足23
* *错误代码： 24“打开的文件太多”*
* *获取错误： 23：打开文件时资源不足*


<u>要再现的步骤：</u>

要检查`/tmp`装载的满度，请在CLI中切换到`/tmp`并运行以下命令：

```bash
 df -h
```

<u>预期的结果</u>：

低于80%。

<u>实际结果</u>：

100%。

## 原因

`/tmp`装载包含的文件过多，原因可能是：

* 错误的SQL查询生成大型和/或过多临时表。
* 服务写入`/tmp`目录。
* 数据库备份/转储保留在`/tmp`目录中。

## 解决方案

您可以执行一些操作以一次性释放一些空间，并且有一些最佳做法可防止`\tmp`变得满满。

### 检查并释放索引节点

确保有足够的可用inode。 为此，请运行以下命令：

```bash
df -i
```

输出将类似于以下内容：

```bash
Filesystem Inodes   Used   Free Use% Mounted on
/dev/nvme2n1 655360    1695  653665    1% /data/mysql
```

检查Use%是否低于70%。 Inode与文件相关联。 如果从分区中删除文件，将释放inode。

### 检查并释放存储空间

有几个服务可能正在将文件保存到`/tmp`。

#### 检查并释放MySQL空间

按照[云基础架构上Adobe Commerce上的MySQL磁盘空间不足>检查并释放支持知识库中的存储空间](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md#check_and_free)中的说明进行操作。

#### 检查Elasticsearch栈转储

>[!WARNING]
>
>栈转储包含可能对调查问题有用的日志记录信息。 考虑将它们存储在单独的位置至少10天。

使用系统外壳程序删除栈转储(`*.hprof`)：

```bash
find /tmp/*.hprof -type f -delete
```

如果您无权删除由另一用户(在本例中为Elasticsearch)创建的文件，但您看到文件很大，请[创建支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)来处理这些文件。

#### 检查数据库转储/备份

>[!WARNING]
>
>数据库备份通常是为了某种目的而创建的。 如果您不确定是否仍需要该文件，请考虑将其移动到单独的位置，而不是删除它。

检查`/tmp`中的`.sql`或`.sql.gz`文件并清理它们。 这些可能是在备份期间或使用`mysqldump`工具手动创建数据库转储时由ece-tools创建的。

### 最佳实践

要避免在`/tmp`已满时出现问题，请遵循以下建议：

* 请勿使用MySQL进行搜索。 Elasticsearch搜索通常无需创建大多数繁重的临时表。 请参阅我们的开发人员文档中的[配置Adobe Commerce以使用Elasticsearch](https://devdocs.magento.com/guides/v2.2/config-guide/elasticsearch/configure-magento.html)。
* 避免在没有索引的列上运行`SELECT`查询，因为这会占用大量临时磁盘空间。 您还可以添加索引。
* 通过在CLI中运行以下命令来创建cron以清理`/tmp`：

  ```bash
  sudo find /tmp -type f -atime +10 -delete
  ```

## 相关阅读

在我们的支持知识库中，[云基础架构上的Adobe Commerce上的MySQL磁盘空间不足](/help/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud.md)。
