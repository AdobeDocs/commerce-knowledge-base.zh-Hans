---
title: ECE-Tools和修补程序更新错误Adobe Commerce云基础架构2.2.x.、2.3.x
description: 本文提供了解决方案，用于解决在尝试将更新部署到ECE-Tools、修补程序或其他更改时，您会看到错误消息，包括“*无法打开流：*”或“*没有此类文件或目录*”。
exl-id: b1658001-0ffd-4f8a-a15f-d785efcee51f
feature: Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# ECE-Tools和修补程序更新错误Adobe Commerce云基础架构2.2.x.、2.3.x

本文提供了解决方案，来解决在尝试将更新部署到ECE-Tools、修补程序或其他更改时，您会看到错误消息，包括“*无法打开流：*”或“*没有此类文件或目录*”。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.2.x.、2.3.x

## 问题

尝试将更新部署到ECE-Tools、修补程序或其他更改时出现的错误包括： Cloud Console和`var/log/cloud.log`中的PHP错误

```
W: PHP Warning: require(<path to file>): failed to open stream: No such file or directory in <path to file> on line 70
W: PHP Fatal error: require(): Failed opening required '<path to file>;'
(include_path='<path to file>') in <path to file> on line 70

Warning: require(/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php):
failed to open stream: No such file or directory in /app/vendor/composer/autoload_real.php
on line 70

Fatal error: require(): Failed opening required '/app/vendor/composer/../../app/etc/NonComposerComponentRegistration.php'
(include_path='/app/vendor/magento/zendframework1/library:.:/usr/share/php')
in /app/vendor/composer/autoload_real.php on line 70

E: Error building project: Step failed with status code 255.
```

异常日志错误：

```
CRITICAL:
error: <path to missing file>: No such file or directory
```

```
W: Generating optimized autoload files
W: PHP Warning: Uncaught ErrorException: require(<path to file>):
failed to open stream: No such file or directory in <path to file>
```

```
PHP Warning: Uncaught Exception: Warning: require(/app/setup/config/application.config.php):
failed to open stream: No such file or directory in /app/vendor/magento/framework/Console/Cli.php
on line 63 in /app/vendor/magento/framework/App/ErrorHandler.php:61
```

```
[Symfony\Component\Console\Exception\CommandNotFoundException]
 W: There are no commands defined in the "module" namespace.
```

## 原因

`composer.json`文件配置错误。

## 解决方案

如果`composer.json`文件中缺少设置，则某些目录将不会从Adobe Commerce代码库中复制。 无法应用包和更新/修补程序，因为找不到文件。

请更改您的额外部分以匹配下面提供的部分，然后重新尝试部署。

```
"extra":{
  "magento-force": true,
  "magento-deploystrategy": "copy"
}
```

## 相关阅读

* 在我们的开发人员文档中[升级和修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/best-practices)。
