---
title: 如果实时网站使用相同的域，则在生产环境中测试Fastly
description: 如果您的生产域(“example.com”)上已启动并运行实时网站，并且您需要在启用了Fastly CDN的云基础架构的生产环境中在Adobe Commerce上测试新存储，我们建议使用子域（如“prod.example.com”）（之前已将它添加到Fastly）来执行任何启动前测试活动。 本文讨论详细信息，并提供指向相关Adobe Commerce文档资源的有用链接。
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# 如果实时网站使用相同的域，则在生产环境中测试Fastly

如果您的生产域(`example.com`)上已启动并运行实时网站，并且您需要在启用了Fastly CDN的云基础架构的生产环境中在Adobe Commerce上测试新存储，我们建议使用子域（例如`prod.example.com`）（以前已将其添加到Fastly）来执行任何启动前测试活动。 本文讨论详细信息，并提供指向相关Adobe Commerce文档资源的有用链接。

## 问题

您当前使用`example.com`生产域的商店已上线并正在运行。 但是，您需要测试新存储，在云基础架构上使用Adobe Commerce构建并部署到生产环境，同时启用Fastly全页缓存服务。

问题是，云基础架构项目上的Adobe Commerce的生产环境使用相同的实时域(`example.com`)，并且您不能在同一域上同时运行当前实时商店将新站点切换到该域。

### 为何使用Fastly在生产环境中进行测试？

理论上，您可以跳过使用Fastly CDN，并在未启用全页缓存的生产环境中的云基础架构存储上测试您的Adobe Commerce。

但是，启用全页缓存后，您的商店的执行方式会有所不同；如果您在启动之前未使用CDN测试过您的网站，则永远无法了解该网站的真实实时性能。 在启用Fastly CDN的情况下在生产环境中测试您的存储是Adobe Commerce的官方建议。

## 解决方案：使用生产子域

在生产环境的云基础架构存储上为新的Adobe Commerce使用第一级子域(`prod.example.com`)，同时将当前实时站点保留在基本域(`example.com`)上。

在云基础架构项目上规划Adobe Commerce时，您可以指定此类生产子域，并请求云基础架构团队将该子域指向Fastly服务。

执行以下步骤，在Adobe Commerce on cloud infrastructure项目中处理子域：

* [提交支持票证](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)，请求将子域添加到Fastly服务/Nginx配置(适用于Adobe Commerce on cloud infrastructure Pro计划架构)。
* 配置您这端的相应DNS设置。

执行子域配置的步骤后，还必须执行以下步骤来验证SSL证书的生产域：

* 上传DNS TXT记录以进行生产域的SSL验证。
* [提交支持票证](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)，请求验证SSL证书的生产域。

使用子域后，您将可以对存储执行“软启动”，因为此类启动只需要更新相应的DNS设置。

## 相关文档

在我们的支持知识库中：

* [在暂存和生产环境中配置Fastly DNS设置](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html)
* [为云上的入门计划设置Fastly](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html)
* 在云基础架构上的Adobe Commerce上启动[个潜在阻止程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html)

在我们的开发人员文档中：

* [Fastly概述](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [上线核对清单： Fastly的DNS配置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html)
