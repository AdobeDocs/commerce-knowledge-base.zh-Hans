---
title: 访问新的集成环境时重定向到父环境
description: 本文为Adobe Commerce提供了有关云基础架构问题的疑难解答说明，在该问题中，尝试访问新创建的集成环境会将您转到父环境。
exl-id: d1d40c8d-d43c-442e-95c9-76f3cdcafb0e
feature: Cache, Integration, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 访问新的集成环境时重定向到父环境

本文为Adobe Commerce提供了有关云基础架构问题的疑难解答说明，在该问题中，尝试访问新创建的集成环境会将您转到父环境。

要解决此问题，您需要更正数据库中的base\_url值，并确保`UPDATE_URLS`变量值设置为`true`。 有关更多详细信息，请参阅以下部分。

受影响的版本和版本：

* 云基础架构上的Adobe Commerce 2.X.X

## 问题

<u>重现步骤</u>：

1. 克隆现有的集成分支。
1. 单击用于访问新环境的URL。

<u>预期的结果</u>：

转到新创建的环境。

<u>实际结果</u>：

您会重定向到父分支上的环境。

## 解决方案

要解决此问题，您需要更正自定义环境数据库中的`base_url`值（安全和不安全），并在`.magento.env.yaml`文件中设置`UPDATE_URL`变量。

### 更正数据库中的base\_url值

如果您使用的是版本2.2.0及更高版本，则可以手动或使用Adobe Commerce CLI更改数据库。

#### 手动更正数据库中的值

1. 连接到数据库。
1. 运行以下命令：

```sql
UPDATE core_config_data SET value = %your_new_environment_unsecure_url% WHERE path="web/unsecure/base_url"
```

```sql
update core_config_data set value = %your_new_environment_secure_url% where path="web/secure/base_url"
```

#### 使用Adobe Commerce CLI更正数据库（适用于版本2.2.X）

1. 以或切换到[Adobe Commerce文件系统所有者](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/web-server/apache.html)身份登录。
1. 运行以下命令：

```bash
php <your_magento_install_dir>/bin/magento config:set web/unsecure/base_url http://example.com
php <your_magento_install_dir>/bin/magento config:set web/secure/base_url https://example.com
```

### 设置`UPDATE_URLS`变量

在本地代码库的`.magento.env.yaml`文件集中：

```
 stage:
    deploy:
        UPDATE_URLS: true
```

### 清除配置缓存

对于要应用的更改，请通过运行以下命令清除配置缓存：

```bash
php <your_magento_install_dir>/bin/magento cache:clean config
```

## 我们的开发人员文档中的相关文章：

[部署变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html)
