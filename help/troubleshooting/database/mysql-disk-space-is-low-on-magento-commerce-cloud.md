---
title: “[!DNL MySQL]磁盘空间在云基础架构上的Adobe Commerce上不足”
description: 本文为您在云基础架构上的Adobe Commerce上遇到空间非常小或 [!DNL MySQL] 没有空间的情况提供了解决方案。 症状可能包括站点中断、客户无法将产品添加到购物车、无法连接到数据库、远程访问数据库、无法通过SSH连接到节点。 症状还包括Galera、环境同步、PHP、数据库和部署错误，如下所列。 单击[解决方案](https://support.magento.com/hc/en-us/articles/360058472572#solution)直接跳转到解决方案部分。
exl-id: 788c709e-59f5-4062-ab25-5ce6508f29f9
feature: Catalog Management, Categories, Cloud, Paas, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---

# 云基础架构上的Adobe Commerce上的[!DNL MySQL]磁盘空间不足

本文为您在云基础架构上的Adobe Commerce上遇到空间非常小或没有空间可供[!DNL MySQL]使用的问题提供了解决方案。 症状可能包括站点中断、客户无法将产品添加到购物车、无法连接到数据库、远程访问数据库、无法通过SSH连接到节点。 症状还包括Galera、环境同步、PHP、数据库和部署错误，如下所列。 单击[解决方案](https://support.magento.com/hc/en-us/articles/360058472572#solution)直接跳转到解决方案部分。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.3.0 - 2.3.6-p1， 2.4.0 - 2.4.2

## 问题

数据库变得太大。 症状可能包括丢失数据库连接、数据库上载错误和各种其他问题。

您可能会遇到的错误：

加莱拉：

* *SQLSTATE\[08S01\]：通信链接失败： 1047 WSREP尚未为应用程序使用准备节点*   *导入错误：*
* *SQLSTATE\[HY000\]：常规错误： 1180获取错误5“输入/输出错误”*
* *SQLSTATE\[08S01\]：通信链接失败： 1047 WSREP尚未为应用程序使用准备节点*

环境同步错误：

* *SQLSTATE：常规错误： 1180在COMMIT*&#x200B;期间收到错误5“输入/输出错误”

php错误：

* *php： PDO：：\_\_construct()： [!DNL MySQL]服务器已消失。*
* *php错误： PDO：：\_\_construct()：读取问候语数据包时出错。 PID=NNNN.*
* *错误2013 (HY000)：在“读取初始通信数据包”时与[!DNL MySQL]服务器失去连接，系统错误： 0“内部错误/检查（非系统错误）”。*

数据库错误：

* *Error\_code： 1114*
* *InnoDB：将word节点写入FTS辅助索引表时出错（磁盘空间不足）。*
* *SQLSTATE\[HY000\]：常规错误： 2006 [!DNL MySQL]服务器已消失*
* *\[ERROR\]从属SQL：错误“表`<table\_name>`已满”。*
* *单元mysql.service进入失败状态。*
* *错误： &#39;无法通过套接字&#39;/var/run/mysqld/mysqld.sock&#39;连接到本地[!DNL MySQL]服务器（111 &#39;连接被拒绝&#39;）&#39;*
* *1205超过锁定等待超时；尝试重新启动事务，查询为： INSERT INTO \&#39;cron\_schedule\&#39; (\&#39;job\_code\&#39;， \&#39;status\&#39;， \&#39;created\_at\&#39;， \&#39;scheduled\_at\&#39;) VALUES (？， ？， `YYYY-02-07 HH:MM:SS`， `YYYY-MM-DD HH:MM:SS`)*

部署错误：

* *E：命令“\[&#39;sudo&#39;， &#39;-u&#39;， `<environment name>`， &#39;bash&#39;， &#39;-c&#39;， &#39;/etc/platform/`<environment name>`/post\_deploy.sh&#39;\]”返回了非零退出状态255*
* *E：命令“\[&#39;ssh&#39;， u`<node IP address>`， &#39;sudo /usr/bin/sv -w 30重新启动站点 — `<environment name>`g-nginx&#39;\]”返回非零*
* *正在升级架构…… SQLSTATE\[HY000\]：常规错误： 1114表`<table\_name>`已满*
* *SQLSTATE\[HY000\]：常规错误： 3写入文件。/`<environment name>`/\#*&#x200B;时出错
* *W： `<filename>` （错误代码： 28“设备上没有剩余空间”）* *索引错误（以及/tmp中孤立的临时.ibd文件）：*
* *目录规则索引器引发异常。 临时表在事后未被清理，然后在当前[!DNL MySQL]主节点*&#x200B;上填充磁盘

<u>重现步骤</u>：

您可以通过在CLI中运行以下命令来检查`/data/mysql`（或无论在何处配置[!DNL MySQL]数据存储）是否已满的一种方法：

```bash
df -h
```

[!DNL MySQL]磁盘上可用内存不足10%是中断的主要指示器。

## 原因

由于一系列问题（如没有足够的inode、可用存储空间以及生成临时表的错误查询），`/data/mysql`装载可能会变满。

## 解决方案

为了使[!DNL MySQL]重回正轨（或防止其卡住），您可以立即执行一个步骤：通过刷新大表格释放一些空间。

但长期解决方案需要分配更多空间并遵循[数据库最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=zh-Hans)，包括启用[订单/发票/装运存档](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/stores-sales/order-management/orders/order-archive)功能。

下面是有关快速解决方案和长期解决方案的详细信息。

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

检查使用%是否低于70%。 Inode与文件相关联。 如果从分区中删除文件，将释放inode。

### 检查并释放存储空间

检查可用的存储空间。 为此，请执行：

```bash
df -k
```

输出将类似于以下内容：

```bash
Size Used Avail Use% Mounted on·
       50G 49G 95M 100% /data/mysql
```

如果“使用%”大于70%，则需要采取措施释放/添加一些空间。

### 检查大型`ibtmp1`文件

检查每个节点`/data/mysql`上的大型`ibtmp1`文件：此文件是临时表的表空间。 如果存在生成临时表的错误查询，则它们包含在`ibtmp1`文件中。 仅当重新启动数据库时才会删除此文件。 如果它正在占用所有可用空间，则必须重新启动数据库。 如果存在错误的查询，则将重新创建它。

### 刷新大型表

>[!WARNING]
>
>我们强烈建议在执行任何操作之前创建数据库备份，并在高站点负载期间避免执行这些操作。 请参阅我们的开发人员文档中的[转储数据库](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)。

检查是否存在大型表格，并考虑是否可以刷新其中的任何表格。 在主（源）节点上执行此操作。

例如，通常可以刷新包含报表的表。 有关如何查找大型表的详细信息，请参阅[查找大型 [!DNL MySQL] 表](/help/how-to/general/find-large-mysql-tables.md)文章。

如果没有大型报表表，请考虑刷新`_index`表，只是为了使Adobe Commerce应用程序返回正轨。 `index_price`个表将是最佳候选。 例如，`catalog_category_product_index_storeX`表，其中X的值可以为“1”到最大存储计数。 请注意，您需要重新索引以恢复这些表中的数据，在大目录的情况下，此重新索引可能需要花费大量时间。

刷新后，请等待wsrep同步完成。 您现在可以创建备份，并采取更多重要步骤来增加空间，例如分配/购买更多空间，以及启用[订单/发票/装运存档](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/stores-sales/order-management/orders/order-archive)功能。

### 检查二进制日志记录设置

检查您的[!DNL MySQL]服务器二进制日志记录设置： `log_bin`和`log_bin_index`。 如果启用这些设置，则日志文件可能会变得很大。 [创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求清除大型二进制日志文件。 此外，请求检查是否正确配置了二进制日志记录，以便定期清除日志并且不会占用太多空间。

如果您无权访问[!DNL MySQL]服务器设置，请请求支持部门进行检查。

### 分配/购买更多空间

如果您有未使用的磁盘空间，请为[!DNL MySQL]分配更多磁盘空间。 请参阅[检查磁盘空间限制](/help/how-to/general/check-disk-space-limit-for-magento-commerce-cloud.md)文章以了解如何检查是否有可用磁盘空间。

* 对于入门计划、所有环境和专业计划集成环境，如果您有一些未使用的磁盘空间，则可以分配磁盘空间。 有关详细信息，请参阅[为 [!DNL MySQL]](/help/how-to/general/allocate-more-space-for-mysql-in-magento-commerce-cloud.md)分配更多空间。
* 对于Pro Plan暂存和生产环境，如果您有一些未使用的空间，请[联系支持人员](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以分配更多磁盘空间。

如果您已达到空间限制但仍遇到空间不足问题，请考虑购买更多磁盘空间，请联系您的Adobe客户团队以了解详细信息。

## 相关阅读

[在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
