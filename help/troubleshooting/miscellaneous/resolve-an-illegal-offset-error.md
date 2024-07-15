---
title: 解决非法偏移错误
description: 本文提供了一个解决方案，用于在Adobe Commerce 2.1或更高版本中，当您在Commerce管理员中创建新产品时收到解决非法偏移错误。
exl-id: 62d16d3c-7f4b-45e9-ae4b-fe2b58cc3620
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 解决非法偏移错误

本文提供了一个解决方案，用于在Adobe Commerce 2.1或更高版本中，当您在Commerce管理员中创建新产品时收到解决非法偏移错误。

在Adobe Commerce 2.1或更高版本中，在Commerce管理员中创建新产品时，可能会显示以下错误：

```text
Warning: Illegal string offset 'is_in_stock' in [...]/vendor/
magento/module-catalog-inventory/Ui/DataProvider/Product/Form/
Modifier/AdvancedInventory.php on line 87
```

## 详细信息

Adobe Commerce 2.1及更高版本在`Magento\Framework\Api\ExtensionAttributesFactory.php`中的[`getExtensionAttributes`](https://github.com/magento/magento2/blob/2.3/lib/internal/Magento/Framework/Api/ExtensionAttributesFactory.php#L64-L73)方法的`getDocComment`验证调用中使用PHP代码注释。

如果您启用了PHP OPcache（我们建议），则会显示此错误，因为默认情况下，OPcache设置[`opcache.save_comments`](http://php.net/manual/en/opcache.configuration.php#ini.opcache.save_comments)处于禁用状态。

## 解决方法

要解决此问题，请找到您的OPcache配置设置并按如下方式启用`opcache.save_comments`：

### 步骤1：找到OPcache配置

#### 要查找OPcache配置设置，请执行以下操作：

PHP OPcache设置通常位于`php.ini`或`opcache.ini`中。 该位置可能取决于您的操作系统和PHP版本。 OPcache配置文件可能具有`[opcache]`部分或类似于`opcache.enable`的设置。

请使用以下指南查找它：

* Apache Web Server：<br>

对于带有Apache的Ubuntu，OPcache设置通常位于`php.ini`中。<br>
对于具有Apache或nginx的CentOS，OPcache设置通常位于`/etc/php.d/opcache.ini`中。<br>
如果没有，请使用以下命令找到它：

```bash
    $ sudo find / -name 'opcache.ini'
```

* PHP-FPM的nginx Web服务器： `/etc/php5/fpm/php.ini`。

如果您有多个`opcache.ini`，请修改全部。


### 步骤2：启用`opcache.save_comments`

1. 在文本编辑器中打开OPcache配置文件。
1. 找到`opcache.save_comments`并取消评论（如有必要）。
1. 确保其值设置为`1`。
1. 保存更改并退出文本编辑器。
1. 重新启动Web服务器：

   * Apache， Ubuntu： `service apache2 restart`
   * Apache， CentOS： `service httpd restart`
   * nginx、Ubuntu和CentOS： `service nginx restart`

1. 重新生成DI配置和所有可自动生成的缺失类：

```bash
    $ bin/magento setup:di:compile`
```
