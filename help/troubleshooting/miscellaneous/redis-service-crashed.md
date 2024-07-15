---
title: Redis服务崩溃
description: 该文章介绍了如何修复Redis。
exl-id: 5eb8fb70-0f41-433a-8d3f-c368781a2d1d
feature: Services
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Redis服务崩溃

该文章介绍了如何修复Redis。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x.、2.3.x
* Adobe Commerce内部部署2.2.x.、2.3x
* Redis的所有版本

## 问题

由于Redis中的内存溢出，网站速度变慢或中断。

## 原因

内存溢出可能导致Redis服务崩溃。 在高峰时段，Redis服务可能需要比当前分配更多的内存。

## 解决方案

要检查当前配置和已使用的内存，请在CLI中运行以下命令。 它检查已用内存、最大内存、已收回密钥和Redis的启动时间（以天为单位）：

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

可从`app/etc/env.php`检索&#x200B;*REDIS\_PORT*&#x200B;和&#x200B;*REDIS\_HOST*&#x200B;变量。

如果运行上述查询的输出显示可用内存的百分比小于40%，则[向Adobe Commerce支持部门提交票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求增加Redis服务器中的`maxmemory`设置。 如果收回的键值不是“0”，或者Redis启动时间（以天为单位）等于0（表示Redis今天已崩溃），则您还应[向Adobe Commerce支持部门提交票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以请求对此问题进行调查和修复。

## 相关阅读

要了解有关Redis内存的更多信息，请参阅[Redis内存优化](https://redis.io/topics/memory-optimization)。
