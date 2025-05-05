---
title: 云上的Adobe Commerce上出现MySQL Server已消失​错误
description: 本文讨论如何解决您在“cron.log”文件中收到“ *SQL server has go away* ”错误消息的问题。 可能会出现一系列症状，包括映像文件导入问题或部署失败。
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 云上的Adobe Commerce上出现MySQL Server已消失&#x200B;错误

本文讨论如何解决您在`cron.log`文件中收到“*SQL Server已不存在*”错误消息的问题。 可能会出现一系列症状，包括映像文件导入问题或部署失败。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 问题

您在`cron.log`文件中收到了“*SQL Server已消失*”错误消息。

<u>重现步骤</u>

导入文件并触发部署。

<u>预期的结果</u>

部署成功。

<u>实际结果</u>

`cron.log`中的错误消息：&quot; *SQLSTATE\[HY000\] \[2006\] MySQL服务器已消失at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php：144&quot;*

## 原因

`default_socket_timeout`值设置过低。 这是由设置`default_socket_timeout`导致的。 如果php在此时间段内未从MySQL数据库收到任何内容，则它会假定已断开连接，并引发错误。

## 解决方案

1. 通过在CLI中运行检查`default_socket_timeout`的当前超时时间段：    ```    php -i |grep default_socket_timeout    ```
1. 根据超时设置的增加，`default_socket_timeout`变量将变为`/etc/platform/<project_name>/php.ini`文件中预期的最长运行时间。 建议你设置10至15分钟。
1. 将其提交到GIT并重新部署。

## 相关阅读

* [数据库上载断开与MySQL的连接](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [云基础架构上Adobe Commerce的数据库最佳实践](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=zh-Hans)
* [Adobe Commerce中关于云基础架构的最常见数据库问题](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=zh-Hans)
