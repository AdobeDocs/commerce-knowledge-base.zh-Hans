---
title: 安装期间，发生反射异常错误
description: 本文针对安装期间出现反射异常错误提供了解决方案。
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# 安装期间，发生反射异常错误

本文针对安装期间出现反射异常错误提供了解决方案。

## 详细信息 {#details}

在安装过程中，会显示与以下内容类似的消息：

```php
[ERROR] exception 'ReflectionException' with message 'Class Magento\Framework\StoreManagerInterface does not exist' in /<path>/lib/internal/Magento/Framework/Code/Reader/ClassReader.php
```

## 解决方案 {#solution}

清除Adobe Commerce的`var`子目录下的所有目录和文件，然后再次安装Adobe Commerce软件。

作为[Adobe Commerce文件系统所有者](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/file-sys-perms-over.html)或具有`root`权限的用户，输入以下命令：

```bash
$ cd <your Magento install directory>/var
```

```bash
$ rm -rf var/cache/* di/* generation/* page_cache/*
```

### Redis {#redis}

如果您使用Redis但仍收到错误，请按如下方式清除Redis缓存：

```bash
$ redis-cli FLUSHALL
```
