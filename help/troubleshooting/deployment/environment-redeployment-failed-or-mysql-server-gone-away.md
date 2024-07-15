---
title: 环境重新部署失败或MySQL服务器消失
description: 本文为Adobe Commerce（所有部署方法）问题提供了一个解决方案，在这些问题中，分配给MySQL的空间中断会导致停滞部署或数据库连接错误。
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 环境重新部署失败或MySQL服务器消失

本文为Adobe Commerce（所有部署方法）问题提供了一个解决方案，在这些问题中，分配给MySQL的空间中断会导致停滞部署或数据库连接错误。

## 受影响的产品和版本

* Adobe Commerce内部部署和Adobe Commerce on cloud基础架构（所有版本）

## 问题

* 部署过程失败，在部署日志（命令行和UI日志）中出现以下错误： ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce以503错误做出响应，并在应用程序日志中显示以下错误消息：    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    并且连接到MySQL服务器时会出现以下错误：    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## 原因

最可能的原因是MySQL数据库分配的空间太小。 要确保出现这种情况，请检查可用于MySQL的空间，如进一步所述。

### 检查是否有足够的空间可供MySQL使用

对于所有Adobe Commerce on cloud infrastructure Starter计划架构环境，以及Adobe Commerce on cloud infrastructure Pro的[集成环境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)计划架构，[SSH到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)并运行命令：

```bash
magento-cloud db:size
```

对于Pro体系结构的暂存或生产环境，[SSH到环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)，然后运行`df -h`   `| grep mysql`命令。 结果将类似于以下内容：

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## 解决方案

### 要解决此问题，您需要为MySQL分配更多空间。

对于所有Starter架构和Pro架构集成环境，可通过增加`mysql: disk:`参数在`.magento/services.yaml`文件中完成此操作。 例如：

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

请参阅[设置MySQL服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html)文章以供参考。

要对Pro体系结构的暂存或生产环境进行这些更改，必须创建[支持票证](https://support.magento.com)。 但通常情况下，您无需在Pro体系结构的测试/生产环境中处理此事件，因为Adobe Commerce会为您监视这些参数并提醒您和/或根据合同采取措施。

### 应用更改

更改`.magento/services.yaml`文件后，您需要提交并推送更改以便应用。 推送将触发部署过程。
