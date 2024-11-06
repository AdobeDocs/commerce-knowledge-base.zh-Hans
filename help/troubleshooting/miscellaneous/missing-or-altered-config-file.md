---
title: 配置文件缺失或更改
description: 解决Adobe Commerce配置文件缺失或更改的问题。
exl-id: d80bf981-8ba6-4357-a841-57bf5d3f2a3f
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# 配置文件缺失或更改

本文介绍如何解决配置文件被更改或丢失的问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

配置文件`config.php`和/或`env.php`被错误更改或丢失。

## 解决方案

部署过程将为每个配置文件创建一个备份文件：

* `app/etc/config.php.bak` — 包含系统特定的设置，如果它不存在，则在生成期间自动生成
* `app/etc/env.php.bak` — 包含敏感配置数据

您可以使用ECE-tools `backup:restore`命令恢复它们。

BAK文件是部署过程的产物。 如果在部署后手动更改配置文件，则您的更改不会反映在现有BAK文件中。

要恢复配置文件：

1. 使用[SSH](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh)登录到远程存储库。
1. 列出可用的备份文件。

   ```
   ./vendor/bin/ece-tools backup:list
   ```

   ```
   The list of backup files:
   app/etc/env.php
   app/etc/config.php
   ```

1. 恢复配置文件。

   ```
   ./vendor/bin/ece-tools backup:restore
   ```

   您会收到受恢复影响的现有配置文件的列表。

   ```
   app/etc/env.php file exists! If you want to rewrite existed files use --force
   app/etc/config.php file exists! If you want to rewrite existed files use --force
   ```

1. 使用`--force`选项覆盖所有文件。

   ```
   ./vendor/bin/ece-tools backup:restore --force
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/env.php was restored.
   Backup file app/etc/config.php was restored.
   ```

1. 或者，您可以恢复特定的配置文件。

   ```
   ./vendor/bin/ece-tools backup:restore --force --file=app/etc/config.php
   ```

   ```
   Command backup:restore with option --force will rewrite your existed files. Do you want to continue [y/N]?y
   Backup file app/etc/config.php was restored.
   ```
