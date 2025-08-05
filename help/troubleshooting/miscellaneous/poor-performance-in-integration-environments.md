---
title: 集成环境中的性能不佳
description: 本文为Pro集成环境和入门暂存环境性能不佳的问题提供了解决方案。
feature: Integration, Staging
role: Developer
exl-id: 46110dbc-2f54-4654-95e2-39e8ae1e6979
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 集成环境中的性能不佳

本文为Pro集成环境和入门暂存环境性能不佳的问题提供了解决方案。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce（所有版本）

## 问题

您的Pro集成环境或入门暂存环境性能不佳。

## 原因

根据您的目录/数据大小或第三方集成/自定义的要求，集成环境中可用的资源可能已超过。

## 解决方案

要解决性能问题，请确保遵循最佳实践以在集成环境中获得最佳性能。 您可能还需要请求升级环境以增强集成。

首先，确定您的环境是否位于[增强集成配置](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-27242)上。

* [专业体系结构](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [入门体系结构](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

使用以下方法之一检查部署日志。

### 方法1：

使用Cloud CLI运行以下命令：

`magento-cloud activity:log -e <branch name>`

### 方法2：

在[Cloud Console](https://console.adobecommerce.com)中查看该环境的最新部署日志。

在部署日志的末尾，如果您看到如下所示的内容（第一行显示大小=XL，其余行显示大小=L ），则表示您使用的是增强型集成配置。

```
Environment configuration
mymagento (type: php:8.2, size: XL, disk: 5120)
mysql (type: mysql:10.6, size: L, disk: 5120)
redis (type: redis:7.2, size: L)
opensearch (type: opensearch:2, size: L, disk: 1024)
rabbitmq (type: rabbitmq:3.12, size: L, disk: 1024)
```

如果您不在增强集成配置中，您可以[请求增强功能/升级](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-27242)。
如果您已在使用增强集成配置，或者在升级后仍遇到性能问题，请确保遵循最佳实践以在集成环境中获得最佳性能：

* [专业体系结构](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment)
* [入门体系结构](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment)

如果您已满足上述建议，请[提交支持请求](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)以获得更多帮助。
