---
title: Redis未序列化错误“设置:static-content:部署”
description: 本文修复了在运行“magento setup:static-content:deploy”时出现Redis未序列化错误的问题。
exl-id: 4bc88933-3bf9-4742-b864-b82d3c1b07a9
feature: Cache, Deploy, Page Content, SCD, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Redis未序列化错误`setup:static-content:deploy`

本文修复了在运行`magento setup:static-content:deploy`时出现Redis未序列化错误的问题。

运行`magento setup:static-content:deploy`导致Redis错误：

```
[Exception]
Notice: unserialize(): Error at offset 0 of 1 bytes in
/var/www/domain.com/vendor/magento/module-config/App/Config/Type/System.php on line 214
```

该问题是由于Redis连接上的并行干扰进程造成的。

要解决此问题，请通过设置以下环境变量，在单线程模式下运行`setup:static-content:deploy`：

```
STATIC_CONTENT_THREADS =1
```

或者，运行`setup:static-content:deploy`命令，后跟`-j 1` （或`--jobs=1` ）参数。

请注意，禁用多线程会减慢部署静态资产的过程。

## 受影响的版本

* Adobe Commerce内部部署：2.1.2及更高版本
* 云基础架构上的Adobe Commerce 2.1.2及更高版本
* Redis，任何版本

## 问题

运行`setup:static-content:deploy`命令导致Redis错误：

```php
)
[2017-06-02 19:57:59] Command:php ./bin/magento setup:static-content:deploy --jobs=3  en_US

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[CredisException]
read error on connection

[RedisException]
read error on connection

.....

[Exception]

Notice: unserialize(): Error at offset 0 of 1 bytes in /app/<domain>/vendor/magento/module-config/App/Config/Type/System.php
on line 214

.....

[RuntimeException]
Command php ./bin/magento setup:static-content:deploy --jobs=3  en_US  returned code 3
```

## 原因

问题是由于Redis连接上的并行干扰进程造成的。

此处，`App/Config/Type/System.php`中的进程需要对`system_defaultweb`的响应，但收到了其他进程对`system_cache_exists`的响应。 查看[Jason Woods帖子](https://github.com/magento/magento2/issues/9287#issuecomment-302362283)中的详细说明。

## 解决方案

通过设置以下环境变量，禁用并行度并在单线程模式下运行`setup:static-content:deploy`：

```
STATIC_CONTENT_THREADS =1
```

也可以运行`setup:static-content:deploy`命令，后跟`-j 1` （或`--jobs=1`）参数。

>[!NOTE]
>
>在单线程模式下，静态内容部署过程可能需要四倍于此的时间。

## 更多信息

在我们的开发人员文档中：

* [配置Redis](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/redis/config-redis.html?lang=zh-Hans)
* [命令行升级](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html?lang=zh-Hans)
