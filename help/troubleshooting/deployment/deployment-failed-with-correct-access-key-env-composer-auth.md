---
title: 在env：COMPOSER_AUTH或auth.json中，部署失败并显示正确的访问密钥
description: 本文为部署失败并出现以下错误“无法下载https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip文件(HTTP/1.1 404 Not Found)”的问题提供了解决方案。
feature: Deploy
role: Admin
exl-id: a18f4213-7381-4001-a5a0-3f8db4525469
source-git-commit: 2a1c97c65282d03010bffabbcd2d1be7fb9ff9a6
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 在env：COMPOSER_AUTH或auth.json中，部署失败并显示正确的访问密钥

本文提供了一个解决方案，用于解决[部署日志](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log)中部署失败并出现以下错误时的问题：

```
W:   [Composer\Downloader\TransportException]
W:   The "https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip" file could not be downloaded (HTTP/1.1 404 Not Found)
```

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.4.x

## 问题

<u>重现步骤</u>：

尝试部署。

<u>预期的结果</u>：

您已成功部署。

<u>实际结果</u>：

>[!NOTE]
>
>这是一个示例错误。 您可能会收到指示其他文件的错误(具体取决于您部署的Adobe Commerce版本)。

您未成功部署。 在[部署日志](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log)中看到&#x200B;*无法下载“https://repo.magento.com/archives/magento/module-customer-balance/magento-module-customer-balance-100.4.0.0.zip”文件(HTTP/1.1 404 Not Found)*&#x200B;之类的错误。

### 原因

在以下位置之一找到的指定编辑器访问键可能无权访问代码：

* 在项目级别的`env:COMPOSER_AUTH`变量中
* 在`auth.json file`中，优先于`env:COMPOSER_AUTH`变量。

### 解决方案

更新项目级别的`env:COMPOSER_AUTH`变量，并确保已为其配置了具有代码访问权限的键。

有关步骤，请参阅Commerce on Cloud Infrastructure指南中的[变量级别](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/variable-levels)。

## 相关阅读

* [无法访问云存储库上的Adobe Commerce：部署时出现403 Forbidden或404 Not Found错误](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)
* [部署错误：下载时发生错误7 ...端口443：连接被拒绝](/help/troubleshooting/deployment/deployment-error-downloading-connection-refused-adobe-commerce.md)
