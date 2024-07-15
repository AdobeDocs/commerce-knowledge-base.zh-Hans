---
title: 安装期间，SessionHandler：：read()出现异常
description: “本文修复了安装Adobe Commerce期间出现的异常**SessionHandler：：read()**错误。”
source-git-commit: 5cec04f8c4f80d34fc26b06eb929960ce21e2dc0
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# 安装期间，SessionHandler：：read()出现异常

本文修复了安装Adobe Commerce期间出现的异常&#x200B;**SessionHandler：：read()**&#x200B;错误。

## 问题

在安装Adobe Commerce的最后一步中，会显示以下异常：

```temrinal
exception 'Exception' with message 'Warning: SessionHandler::read():
open(..) failed: No such file or directory (2) ../magento2/lib/internal/Magento/Framework/Session/SaveHandler.php on line 74'
in ../magento2/lib/internal/Magento/Framework/App/ErrorHandler.php:67
```

>[!NOTE]
>
>此错误仅发生在2015年9月28日之前的代码版本中。 如果您安装的代码日期为9月29日或更高版本，则不会出现此错误。 有关Redis配置选项的更多信息，请参阅我们的开发人员文档中的[配置Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)。 有关使用命令行安装程序指定Redis的详细信息，请参阅我们的开发人员文档中的[安装主题](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-install.html)或[部署配置主题](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp)。

## 原因

当将`session.save_handler` PHP参数设置为比`files`更多的会话存储（例如，`redis`、`memcached`等）时，会发生这种情况。 这是一个我们正在努力解决的已知问题。

## 解决方案：

* 升级您的Adobe Commerce代码。 请参阅我们的开发人员文档中的[安装指南>更新Adobe Commerce软件](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall.html#instgde-install-magento-update)。
* 对现有代码使用以下解决方法：

## 找到`php.ini` {#locate-php-ini}

通过输入以下命令找到`php.ini`：

```php
php -i | grep "Loaded Configuration File"
```

典型位置如下：

* Ubuntu： `/etc/php5/cli/php.ini`
* CentOS： `/etc/php.ini`

## 解决方法 {#workaround}

1. 作为具有`root`权限的用户，在文本编辑器中打开`php.ini`。
1. 找到`session.save_handler`
1. 通过以下任一方式设置它：
   * 要对此进行评论，请执行以下操作：

     ```php
     ;session.save_path = <path>
     ```

   * 要将其设置为文件系统路径，请执行以下操作：

     ```php
     session.save_handler = files
     ```
