---
title: 无法使用nginx进行安装
description: 本文修复了使用nginx Web服务器时Adobe Commerce安装失败的问题。
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# 无法使用nginx进行安装

本文修复了使用nginx Web服务器时Adobe Commerce安装失败的问题。

## 问题

如果您使用nginx Web服务器并尝试安装Adobe Commerce软件，则安装有时会失败。

## 解决方案

您可以通过中的以下错误确认问题 `var/report` 目录：

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### 解决方法

使用安装Adobe Commerce软件 [命令行](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli.html).
