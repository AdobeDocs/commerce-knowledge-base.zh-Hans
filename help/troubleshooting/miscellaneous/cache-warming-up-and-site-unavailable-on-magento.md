---
title: 缓存预热和网站在Adobe Commerce上不可用
description: 本文为页面缓存预热并且存在停滞部署或站点关闭时提供了一个解决方案。
exl-id: c91d5c1f-95e6-4240-be98-2acea49ae728
feature: Cache, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# 缓存预热和网站在Adobe Commerce上不可用

本文为页面缓存预热并且存在停滞部署或站点关闭时提供了一个解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 问题

在部署后阶段结束时，高速缓存预热脚本以极高的速率发送请求，以致于某些实例（如4-cpu实例）无法处理。 他们的nginx耗尽了工人的数量。

<u>重现步骤</u>：

启动缓存预热操作。

<u>预期的结果</u>：

页面或整个网站加载。

<u>实际结果</u>：

站点不可用或响应时间太长。

## 解决方案

限制缓存预热期间的并发连接数。 这需要添加`WARM_UP_CONCURRENCY`部署后变量以指定缓存预热脚本可同时发送的预热请求数。 设置此选项有助于管理Adobe Commerce云基础架构的负载。 有关步骤，请参阅我们的开发人员文档中的[部署后变量> WARM\_UP\_CONCURRENCY](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-post-deploy#warm_up_concurrency)。

## 相关阅读

我们用户指南中的[全页缓存](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#full-page-caching)
