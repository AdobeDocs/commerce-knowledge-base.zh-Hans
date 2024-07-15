---
title: Web API无法处理数组中超过20个项目的请求
description: 本文为Web API无法处理数组中Adobe Commerce 2.4.3包含20个以上项目的消息的问题提供了解决方案。
exl-id: 7e6b3fe8-3133-4773-afa7-fbfdd98ecde9
feature: REST
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# Web API无法处理数组中超过20个项目的请求

本文为Web API无法处理数组中Adobe Commerce 2.4.3包含20个以上项目的消息的问题提供了解决方案。

## 受影响的产品和版本：

* Adobe Commerce（所有部署方法） 2.4.3和2.3.7-p1
* Magento Open Source2.4.3和2.3.7-p1

## 问题

Web API无法处理数组中包含20个以上项目的消息（例如，库存更新）。

## 原因

在Adobe Commerce 2.4.3中，为MagentoAPI添加了内置速率限制功能，以防止拒绝服务(DoS)攻击。

默认情况下，可以使用以下内置API速率限制：

* 包含表示实体列表的输入的REST请求默认最多为20个实体
* 允许分页结果的REST和GraphQL查询默认每页最多300个项目

## 解决方案

要禁用REST API请求的输入限制，请应用以下修补程序之一（具体取决于您的版本）：

* [MC-43048__set_rate_limits__2.3.7-p1.patch.zip](assets/MC-43048__set_rate_limits__2.3.7-p1.patch.zip)
* [MC-43048__set_rate_limits__2.4.3.patch.zip](assets/MC-43048__set_rate_limits__2.4.3.patch.zip)

### 兼容的Adobe Commerce版本

修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.4.3和2.3.7-p1
* Adobe Commerce内部部署2.4.3和2.3.7-p1

这些修补程序与任何其他Adobe Commerce版本不兼容。

### 如何应用修补程序

解压缩下载的`.zip`文件并应用[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序中所述的修补程序。

>[!WARNING]
>
>如果您怀疑存储区正在遭受DoS攻击，Adobe建议将默认输入限制降低到较低的值，以限制可请求的资源数量。  您可以使用[类构造函数参数](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html)以编程方式自定义默认限制
>如我们的开发人员文档中所述：[API安全>速率限制>最大参数输入](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting)。

## 相关阅读

在我们的开发人员文档中，[API安全>速率限制](https://devdocs.magento.com/guides/v2.4/get-started/api-security.html#rate-limiting)。
