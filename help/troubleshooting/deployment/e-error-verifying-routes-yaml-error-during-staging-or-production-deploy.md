---
title: 'E：验证routes时出错。在暂存或生产部署期间出现yaml错误'
description: '本文为Adobe Commerce提供了云基础架构问题的解决方案，其中您会收到*"E：验证路由时出错.yaml"*错误消息，此消息旨在尝试将项目部署到暂存或生产环境。'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E：验证路由时出错。在暂存或生产部署期间出现yaml错误

本文为Adobe Commerce提供了云基础架构问题的解决方案，其中您收到&#x200B;*&quot;E：验证routes.yaml时出错&quot;*&#x200B;错误消息，当时尝试将项目部署到暂存或生产环境。

## 受影响的版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

<u>重现步骤</u>：

通过将代码推送到暂存或生产环境来触发部署。

<u>预期行为</u>：

部署成功。

<u>实际行为</u>：

部署被阻止，日志中显示以下错误消息：

<pre>部署应用程序验证配置E：验证routes.yaml时出错。
为您的群集配置了以下域，但未在routes.yaml文件中定义路由：

- store1.example.com
- store2.example.com
- test-store.example.com

使用当前的routes.yaml配置，
  这些域将无法提供服务！

要继续，请参阅此处获取疑难解答说明：
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## 原因

如果`routes.yaml`文件中缺少已添加到项目中的任何其他域的路由配置，则会出现此错误。

作为自助路由配置的Adobe Commerce自助启用升级的一部分，我们添加了部署前检查，以确保项目中的所有域已在`routes.yaml`文件中配置路由。 如果有任何域缺少路由配置，则会阻止部署。

## 解决方案

若要解决阻止的部署，请使用以下任一方法更新`routes.yaml`文件，以便为错误消息中列出的域配置路由：

* 在升级过程中应用Adobe Commerce提供的修补程序。
* 手动将缺少的路由配置添加到`routes.yaml`文件。

### 方法1：应用Adobe Commerce提供的修补程序

1. 查找标题为“*为&lt;project\_ID>启用自助服务功能”的最新Adobe Commerce支持票证。*
1. 按照票证中的说明应用补丁程序，这会更新云环境的路由配置。
1. 提交с并推送更改以重新部署项目。

### 方法2：手动添加缺少的路由配置

1. 要使用相同的路由配置为项目中的所有域提供服务，请更新`routes.yaml`文件，为项目中的默认域和所有其他域添加路由模板，如以下示例所示：

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. 提交с并推送更改以重新部署项目。

有关更新路由配置的详细说明，请参阅我们的开发人员文档中的[Adobe Commerce云>配置路由](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html)。

>[!NOTE]
>
>如果项目配置指定了不再使用的域，请完成以下步骤以便尽早从项目中将其删除： 1. 提交支持工单，其中包含要从项目环境中移除的域的列表。 2.支持团队删除域后，更新`routes.yaml`文件以删除对过时域的任何引用。
