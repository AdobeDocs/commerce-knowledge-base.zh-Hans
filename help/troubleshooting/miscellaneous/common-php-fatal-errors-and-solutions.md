---
title: 常见PHP致命错误和解决方案
description: 本文列出了在查看Adobe Commerce日志时可以找到的一些常见的PHP致命错误快速示例，以及它们指示的问题的解决方案。
exl-id: 3e42d38f-97bc-4d38-8e36-23b1453f81d9
feature: Support
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# 常见PHP致命错误和解决方案

本文列出了在查看Adobe Commerce日志时可以找到的一些常见的PHP致命错误快速示例，以及它们指示的问题的解决方案。

## 示例

*&#39;PHP致命错误：在....&#39;*&#x200B;中超出了60秒的最大执行时间

## 解决方案

您可以通过在`php.ini`文件中设置自定义`max_execution_time`值并重新部署来更新最大执行时间。

例如：

`max_execution_time = 120`

请参阅[自定义php.ini设置](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html)一文。

## 示例

*&#39;PHP严重错误：允许的内存大小已用完792723456字节&#39;* （这只是示例字节大小。）

## 解决方案

自定义您的`php.ini`设置。 请参阅此[自定义php.ini设置](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html)文章。

## 示例

*&#39;PHP警告：未知：无法打开流：没有这样的文件或目录&#39;*

## 解决方案

确保未删除`php.ini`文件中的Windows样式结尾。 在Windows上，行尾由回车（ASCII 0x0d或\r）和新行(\n)的组合终止，也称为CR/LF。

## 示例

*&#39;PHP严重错误：未捕获的PDOException： SQLSTATE\[HY000\] \[1040\]&#39;*&#x200B;中的连接太多

## 解决方案

MySQL环境的磁盘空间不足。 为MySQL环境提供更多磁盘空间。

## 示例

*&#39;PHP致命错误：未捕获的TypeError：返回Magento&#39;*&#x200B;的值

## 解决方案

检查`<root>/tmp`目录，因为它可能已满。 如果空间已满，请在目录中提供更多空间。 这可能只是将文件移动到另一个目录或删除它们。

## 相关阅读

在我们的开发人员文档中：

* [PHP设置错误](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html)
* [必需的PHP设置](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)
* [Redis验证](https://devdocs.magento.com/guides/v2.3/config-guide/redis/redis-session.html#redis-verify)
* [配置Redis](https://devdocs.magento.com/guides/v2.3/config-guide/redis/config-redis.html)
* [PHP内存限制错误](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/php/tshoot_php-set.html#trouble-php-memory)
* [常见问题的解决方案 — 内存限制](https://devdocs.magento.com/guides/v2.3/test/unit/unit_test_execution_cli.html#solutions-to-common-problems)
