---
title: 备份问题
description: 本文列出了针对备份创建问题的可能解决方案。
exl-id: 1a6204ad-bd5a-46dc-8a8e-39655a174e09
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# 备份问题

本文列出了针对备份创建问题的可能解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署2.3.x
* Magento Open Source2.3.x

## 已禁用备份 {#backup-disabled}

如果Adobe Commerce备份功能未启动或显示以下消息，则需要在备份之前启用该功能。

```bash
Backup functionality is disabled.
Backup functionality is currently disabled. Please use other means for backups.
```

输入以下CLI命令：

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

有关备份的其他信息，请参阅[备份和回滚文件系统、介质和数据库。](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/backup)

## 磁盘空间不足 {#insufficient-disk-space-trouble-backup-space-}

如果由于磁盘空间不足导致备份失败，通常应通过将某些文件移动到其他存储设备或驱动器来释放磁盘空间。 但是，可能有其他方法来解决此问题。 有关提示，请参阅以下资源之一：

* 解决Linux和Unix系统硬盘问题的[8提示，例如磁盘已满或无法写入磁盘](https://www.cyberciti.biz/datacenter/linux-unix-bsd-osx-cannot-write-to-hard-disk)
* [serverfault： df表示磁盘已满，但磁盘未满](https://serverfault.com/questions/315181/df-says-disk-is-full-but-it-is-not)
* [unix.stackexchange.com：在Linux上跟踪磁盘空间的使用情况？](https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux)

## 操作系统错误 {#operating-system-error-trouble-backup-os-}

很遗憾，由于您可能会遇到各种错误，我们无法推荐任何特定的内容。 不过，我们可以建议您：

* 请与系统管理员联系。
* 搜索公共论坛，如[栈栈Exchange](https://unix.stackexchange.com)或[栈栈溢出](https://stackoverflow.com)
* 打开[GitHub问题](https://github.com/magento/magento2/issues)，我们将尝试提供帮助。

## 备份失败 {#backup-fails-trouble-backup-all-}

如果备份失败或所有备份测试都失败，则[Adobe Commerce文件系统所有者](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)可能没有足够的特权和所有权来拥有Adobe Commerce文件系统。 例如，其他用户可能拥有这些文件或者这些文件可能是只读的。

请特别注意`<magento_root>/var`目录和子目录的文件系统权限和所有权。 有关详细信息，请参阅[设置文件系统权限和所有权](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/configure-permissions)。
