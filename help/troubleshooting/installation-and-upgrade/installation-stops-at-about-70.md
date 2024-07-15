---
title: 安装停止率约为70%
description: 本文为安装停止在70%左右时提供了修补程序。
exl-id: 04aa3572-3c42-4565-9f7f-b4d90df96df2
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 安装停止率约为70%

本文为安装停止在70%左右时提供了修补程序。

## 问题

在使用安装向导进行安装期间，该过程将在大约70%时停止（无论是否包含示例数据）。 屏幕上不显示错误。

## 原因

此问题的常见原因包括：

* [`max_execution_time`](http://php.net/manual/en/info.configuration.php#ini.max-execution-time)的PHP设置
* nginx和Varnish的超时值

## 解决方案：

根据需要设置以下所有内容。

### 所有Web服务器和Varnish {#all-web-servers-and-varnish}

1. 使用[`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo)文件找到您的`php.ini`。
1. 作为具有`root`权限的用户，在文本编辑器中打开`php.ini`。
1. 找到`max_execution_time`设置。
1. 将其值更改为`18000` 。
1. 将更改保存到`php.ini`并退出文本编辑器。
1. 重新启动Apache：

   * CentOS： `service httpd restart`
   * Ubuntu： `service apache2 restart`

   如果您使用nginx或Varnish，请继续下列各节。

### 仅限nginx {#nginx-only}

如果您使用nginx，请使用我们包含的`nginx.conf.sample`或在nginx主机配置文件中将超时设置添加到`location ~ ^/setup/index.php`部分，如下所示：

```php
location ~ ^/setup/index.php {
    .....................
    fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
}
```

重新启动nginx： `service nginx restart`

### 仅涂漆 {#varnish-only}

如果您使用Varnish，请编辑`default.vcl`并向`backend`段添加超时限制值，如下所示：

```php
backend default {
.....................
      .first_byte_timeout = 600s;
}
```

重新启动Varnish。

```php
service varnish restart
```
