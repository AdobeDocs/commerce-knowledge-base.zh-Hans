---
title: 用于隐藏类别的GraphQL查询不适用于B2B共享目录
description: 本文提供了一个解决方案，用于在B2B共享目录功能不适用于GraphQL类别查询时隐藏类别。
exl-id: bdafa8d9-b637-409e-86b5-d132bccfe0b8
feature: B2B, Catalog Management, Categories, GraphQL, Customer Service
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# 用于隐藏类别的GraphQL查询不适用于B2B共享目录


## 受影响的产品和版本

* 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.4.3

## 问题

GraphQL类别和`categoryList`查询忽略类别权限以隐藏共享目录中的类别。 在B2B共享目录功能开启的情况下，Adobe Commerce 2.4.3上的所有商家都会发生这种情况。

<u>重现步骤</u>：

先决条件：

这种情况发生在Adobe Commerce 2.4.3上的所有商户上，这些商家的PWA店面使用带有Adobe Commerce后端/管理员的GraphQL API，并且启用了B2B共享目录功能。

1. 创建多个类别(CAT1、CAT2)。
1. 创建专用共享目录。
1. 创建公司用户并将其分配给上述共享目录。
1. 为每个类别分配一些产品。
1. 将CAT1分配给自定义目录，从自定义专用目录中取消分配CAT2。 这会从共享目录中取消分配CAT2中的所有产品。
1. 保存自定义目录。
1. 将CAT2的类别权限设置为&#x200B;*拒绝*&#x200B;浏览类别，并将客户组设置为上述专用目录。
1. 以步骤3中的公司用户身份运行`categoryList query`或类别查询。

<u>预期的结果</u>：

结果中只显示CAT1。

<u>实际结果</u>：

所有类别都会显示，无论它们在共享目录中是否已分配/取消分配，或者类别权限是什么。

## 原因

功能未实现。

## 解决方案

该问题将在版本2.4.4的范围内修复，如果商家需要2.4.4版本之前的解决方案，他们应[提交票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以获取自定义修补程序。

## 相关阅读

* [最佳实践Adobe Commerce支持知识库中的类别数限制](https://support.magento.com/hc/en-us/articles/360048176832)。
