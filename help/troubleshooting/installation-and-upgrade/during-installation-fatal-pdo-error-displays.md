---
title: 安装期间显示严重的PDO错误
description: 本文修复了安装过程中出现的异常严重PDO错误。
exl-id: d69908f0-71c9-48de-9369-6ada22f2b393
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 0%

---

# 安装期间显示严重的PDO错误

本文修复了安装过程中出现的异常严重PDO错误。

## 问题

```php
PHP Fatal error:  Class 'PDO' not found in /var/www/html/magento2/setup/module/Magento/Setup/src/Module/Setup/ConnectionFactory.php on line 44
```

## 解决方案

确保安装所有[必需的PHP扩展](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html)。
