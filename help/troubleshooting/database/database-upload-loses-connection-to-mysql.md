---
title: 数据库上载断开与MySQL的连接
description: 本文为数据库上载丢失与MySQL的连接提供了一种解决方案。
exl-id: 6051cea1-8292-4a81-8908-eb516cb4a32b
feature: Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# 数据库上载断开与MySQL的连接

本文为数据库上载丢失与MySQL的连接提供了一种解决方案。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.2.x.、2.3.x

## 问题

数据库无法上传到云基础架构上的Adobe Commerce上的主/集成分支专业规划架构或Adobe Commerce上的任何分支云基础架构入门规划架构，症状是无法连接。 您在CLI中看到此错误。

```
web@ddc35c264bd89a72042f1f3e5a:~$ mysql -h database.internal -u user -p main
Enter password:
ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"
```

## 原因

这通常是由于缺少用于导入数据库的磁盘空间。

## 解决方案

检查磁盘空间是否不足。 为此，请在CLI中针对数据库端口3306运行`netcat`命令；如果磁盘已满，将显示磁盘已满消息：

```
web@ddc35c264bd89a72042f1f3e5a:~$ nc database.internal 3306
Database out of space
```

您需要为`services.yaml`中的数据库分配更多空间，如果有些空间未使用，则进行部署。 有关步骤，请参阅[服务磁盘空间](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#service-disk-space)。

注意：在Pro体系结构计划上，可以通过运行以下命令来检查分区上的已分配空间： `df -h`

预期输出类似于以下输出。 在此示例中，使用分配的25GB中的10GB，而不使用15GB的MySQL空间。

```
f240jestone3wt@i-087r2a25fdac80726:~$ df -h|grep 'File\|xvd'
Filesystem                                         Size  Used Avail Use% Mounted on
/dev/xvda1                                          59G   15G   42G  26% /
/dev/xvdj                                           25G   10G   15G  41% /data/mysql
/dev/xvdi                                           25G   22G  2.6G  90% /data/exports
```

## 相关阅读

在我们的开发人员文档中[管理磁盘空间](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space)
