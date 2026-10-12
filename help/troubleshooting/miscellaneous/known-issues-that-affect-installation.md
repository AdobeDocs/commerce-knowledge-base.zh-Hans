---
title: 影响xdebug安装的已知问题
description: 本文提供了在使用可选PHP扩展“xdebug”时遇到异常错误时的解决方案。
exl-id: 5090ea99-e0c3-436a-809b-109701740927
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%
---
# 影响xdebug安装的已知问题

本文提供了在使用可选PHP扩展`xdebug`时遇到异常错误时的解决方案。

* 安装期间
* 成功安装后访问Commerce管理员或店面

示例异常：

```php
Fatal error: Maximum function nesting level of '100' reached, aborting!
```

要解决此问题，您可以：

* 禁用`xdebug`扩展。
* 将`xdebug.max_nesting_level`的值设置为200或更大的值。 有关详细信息，请参阅[xdebug文档](http://xdebug.org/docs/basic#max_nesting_level)。

更改或禁用`xdebug`的配置后，重新启动Apache：

* CentOS： `sudo service httpd restart`
* Ubuntu： `sudo service apache2 restart`
