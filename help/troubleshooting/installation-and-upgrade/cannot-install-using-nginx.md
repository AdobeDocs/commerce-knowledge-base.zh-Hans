---
title: 无法使用nginx进行安装
description: 本文修复了使用nginx Web服务器时Adobe Commerce安装失败的问题。
exl-id: 0af90c7e-0733-41c8-b217-9595b133fa95
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '87'
ht-degree: 0%

---

# 无法使用nginx进行安装

本文修复了使用nginx Web服务器时Adobe Commerce安装失败的问题。

## 问题

如果您使用nginx Web服务器并尝试安装Adobe Commerce软件，则安装有时会失败。

## 解决方案

您可以在`var/report`目录中通过以下错误确认问题：

```php
NOTE: You cannot install Adobe Commerce using the Setup Wizard because the Adobe Commerce setup directory cannot be accessed.
You can install Adobe Commerce using either the command line or you must restore access to the following directory: /var/www/html/setup
If you are using the sample nginx configuration, please go to http://ce.mtf03.bcn.magento.com/setup/";i:1;s:641:"#0 /var/www/html/lib/internal/Magento/Framework/App/Http.php(213): Magento\Framework\App\Http->redirectToSetup(Object(Magento\Framework\App\Bootstrap), Object(Exception))
```

### 解决方法

使用[命令行](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/advanced)安装Adobe Commerce软件。
