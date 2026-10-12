---
title: 安装期间，发生反射异常错误
description: 本文针对安装期间出现反射异常错误提供了解决方案。
exl-id: aed5f297-1339-4171-9392-04b3f93277ee
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '107'
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

作为[Adobe Commerce文件系统所有者](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)或具有`root`权限的用户，输入以下命令：

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
