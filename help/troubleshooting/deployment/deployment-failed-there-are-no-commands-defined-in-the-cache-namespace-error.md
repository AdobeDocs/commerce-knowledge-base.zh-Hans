---
title: “部署在缓存刷新时失败：‘缓存’命名空间中未定义命令’错误”
description: 本文为部署失败并出现以下错误**在缓存命名空间中未定义命令**的问题提供了解决方案。
feature: Deploy
role: Developer
exl-id: ee2bddba-36f7-4aae-87a1-5dbeb80e654e
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# 部署在缓存刷新时失败：“在‘缓存’命名空间中未定义命令”错误

>[!WARNING]
>
>在执行这些步骤之前，请先在实时生产站点中备份数据库。

本文为部署失败并且日志中的错误之一类似以下时的问题提供了解决方案：

```
[YEAR-DAYTIME] ERROR: [127] The command "php ./bin/magento cache:flush --ansi --no-interaction" failed.
        There are no commands defined in the "cache" namespace.
...
      W:     There are no commands defined in the "cache" namespace.
```

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.4.x

## 问题

<u>重现步骤</u>：

尝试部署。

<u>预期的结果</u>：

您已成功部署。

<u>实际结果</u>：

您未成功部署。 在日志中，您看到一个部署错误，其消息类似于以下&#x200B;*缓存命名空间*&#x200B;中没有命令。

### 原因

**`core_config_data`**&#x200B;表包含数据库中不再存在的商店ID或网站ID的配置。 当您从另一个实例/环境导入了数据库备份，并且这些作用域的配置保留在数据库中时会发生这种情况，尽管关联的存储/网站已被删除。

### 解决方案

如果您只有一个网站，则对这些网站的第二次测试不适用，并且您只需要测试商店。

要解决此问题，请确定这些配置中剩余的无效行。

1. SSH到服务器并运行此命令：

   `bin/magento`

1. 该错误消息可能指示哪些行和表保留在已删除站点的数据库中。 例如，以下错误表示未找到所请求的存储：

   ```...
   In StoreRepository.php line 112:
   
   The store that was requested wasn't found. Verify the store and try again.
   ```

1. 运行此[!DNL MySQL]查询以验证是否找不到存储，如步骤2中的错误消息所示。

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 运行以下[!DNL MySQL]语句以删除无效行：

   ```sql
   delete from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 再次运行此命令：

   `bin/magento`

   如果您收到如下错误，这表示未找到所请求的ID为X的网站，则表示您剩余有配置        删除的网站和商店中的数据。

   ```
   In WebsiteRepository.php line 110:
   
   The website with id X that was requested wasn't found. Verify the website and try again.
   ```

   运行此[!DNL MySQL]查询并验证是否找不到该网站：

   ```sql
   select distinct scope_id from core_config_data where scope='stores' and scope_id not in (select store_id from store);
   ```

1. 运行此[!DNL MySQL]语句以从网站配置中删除无效行：

   ```sql
   delete from core_config_data where scope='websites' and scope_id not in (select website_id from store_website);
   ```

要确认解决方案是否有效，请再次运行`bin/magento`命令。 您应该不会再看到错误，并且可以成功部署。

## 相关阅读

* [Adobe Commerce部署疑难解答程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-deployment-troubleshooter)
* [如果Cloud UI出现“日志截断”错误，则检查部署日志](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
