---
title: 安装可选示例数据时出错
description: 本主题讨论安装可选示例数据时可能遇到的错误的解决方案。
exl-id: 14692e3a-188c-45f1-9df5-ac873cc9eff0
feature: Console, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# 安装可选示例数据时出错

本主题讨论安装可选示例数据时可能遇到的错误的解决方案。

## 症状（文件系统权限）

使用安装向导安装示例数据期间控制台日志中出错：

```php
Module 'Magento_CatalogRuleSampleData':
[ERROR] exception 'Magento\Framework\Exception\LocalizedException' with message 'Can't create directory /var/www/html/magento2/generated/code/Magento/CatalogRule/Model/.' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Generator.php:103

(more)

Next exception 'ReflectionException' with message 'Class Magento\CatalogRule\Model\RuleFactory does not exist' in /var/www/html/magento2/lib/internal/Magento/Framework/Code/Reader/ClassReader.php:29

(more)
```

这些异常由文件系统权限设置产生。

### 解决方案

[再次设置文件系统所有权和权限](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=zh-Hans)作为具有`root`权限的用户。

## 症状（生产模式）

如果当前设置为[生产模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=zh-Hans)，则使用[magento sampledata：deploy](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/sample-data/composer-packages.html?lang=zh-Hans)命令时，示例数据安装将失败：

```php
PHP Fatal error: Uncaught TypeError: Argument 1 passed to Symfony\Component\Console\Input\ArrayInput::__construct() must be of the type array, object given, called in /<path>/vendor/magento/framework/ObjectManager/Factory/AbstractFactory.php on line 97 and defined in /<path>/vendor/symfony/console/Symfony/Component/Console/Input/ArrayInput.php:37
```

### 解决方案

请勿在生产模式下安装示例数据。 切换到开发人员模式并清除某些`var`目录，然后重试。

按照[Adobe Commerce文件系统所有者](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/file-system/overview.html?lang=zh-Hans)显示的顺序输入以下命令：

```php
cd <magento_root>
bin/magento deploy:mode:set developer
rm -rf generated/code/* generated/metadata/*
bin/magento sampledata:deploy
```

## 症状（安全性）

在安装可选的示例数据期间，会显示一条与以下内容类似的消息：

```php
PHP Fatal error: Call to undefined method Magento\Catalog\Model\Resource\Product\Interceptor::getWriteConnection() in /var/www/magento2/app/code/Magento/SampleData/Module/Catalog/Setup/Product/Gallery.php on line 144
```

### 解决方案

在示例数据安装过程中，使用如下资源禁用SELinux：

* [www.ibm.com](https://www.ibm.com/docs/ja/ahts/4.0?topic=t-disabling-selinux)
* [CentOS文档](https://docs.centos.org/en-US/docs/)

## 症状（开发分支）

显示其他错误，例如：

```php
[Magento\Setup\SampleDataException] Error during sample data installation: Class Magento\Sales\Model\Service\OrderFactory does not exist
```

### 解决方案

在Adobe Commerce开发分支中使用示例数据时存在已知问题。 请改用主分支。 您可以按如下方式切换到主分支：

```php
cd <magento_root>
git checkout master
git pull origin master
```

## 症状(max_execution_time)

安装将在示例数据安装完成之前停止。 下面是一个示例：

```php
(more)

Module 'Magento_CustomerSampleData':
Installing data...
```

示例数据安装未完成。

当超过PHP脚本配置的最大执行时间时，会发生此错误。 由于加载示例数据可能需要较长时间，因此您可以在安装期间增加值。

### 解决方案

作为具有`root`权限的用户，请修改`php.ini`以将`max_execution_time`的值增加到600或更多。 (600秒是10分钟。 您可以根据需要增加值。) 安装成功后，您应将`max_execution_time`更改回其先前的值。

如果您不确定`php.ini`的位置，请输入以下命令：

```php
php --ini
```

`Loaded Configuration File`的值是您必须修改的`php.ini`。

>[!NOTE]
>
>我们知道，本文可能仍然包含行业标准的软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。
