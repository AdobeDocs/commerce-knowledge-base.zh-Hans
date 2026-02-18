---
title: 部署时出现“不支持当前版本的RDBMS”错误
description: 本文提供了当部署失败并在部署日志中出现以下错误时的解决方案： *当前版本的RDBMS不受支持*。
exl-id: e7300f64-5749-4de8-b4d2-bc4789437282
feature: Deploy
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# 部署时出现“不支持当前版本的RDBMS”错误

本文为部署失败并在部署日志中出现以下错误时提供了解决方案： *当前版本的RDBMS不受支持*。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，从2.3.0到2.3.7-p1，从2.4.0到2.4.3。

## 问题

此错误消息表示您尝试升级到的Adobe Commerce版本不再支持当前的MariaDB版本，必须将MariaDB升级到兼容版本。


<u>重现步骤</u>：

尝试部署。

<u>预期的结果</u>：

部署成功。

<u>实际结果</u>：

部署失败，并出现错误消息： *当前版本的RDBMS不受支持*。

## 原因

您的MariaDB版本与您尝试升级到的Adobe Commerce版本不兼容。

## 解决方案

在升级应用程序之前，必须将MariaDB服务升级到兼容版本。


对于云基础架构Pro计划架构上Adobe Commerce的集成分支（以及入门架构中的所有分支），请按照开发人员文档中的[配置服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/service/services-yaml)操作。

对于云基础架构Pro计划架构上的Adobe Commerce上的暂存和生产，请[提交支持票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)以请求在您部署Adobe Commerce版本升级之前升级服务。


## 相关阅读

* 在开发人员文档中[生成和部署的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)。
* [Adobe Commerce 2.3.5升级：在我们的支持知识库中压缩到动态表](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html?lang=zh-Hans)。
