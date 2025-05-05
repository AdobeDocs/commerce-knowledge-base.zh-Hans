---
title: 减少云基础架构上Adobe Commerce的部署停机时间
description: 为了显着减少维护停机时间并提供跨环境存储的高效配置，云基础架构上的Adobe Commerce提供了**配置管理**功能。 对于云基础架构2.2.x及更高版本实施上的Adobe Commerce，此功能通过减少步骤支持管道部署概念和选项。
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# 减少云基础架构上Adobe Commerce的部署停机时间

为了显着减少维护停机时间并提供跨环境存储的高效配置，云基础架构上的Adobe Commerce提供了&#x200B;**配置管理**&#x200B;功能。 对于云基础架构2.2.x及更高版本实施上的Adobe Commerce，此功能通过减少步骤支持管道部署概念和选项。

## 概述

部署Web应用商店时遇到的痛苦且耗时的问题包括：

* **在所有环境中应用相同的配置。**&#x200B;通常，您可以手动输入配置，或通过复杂的数据库更新输入配置。 使用配置管理，可将配置从数据库导出到单个文件中，以便稍后使用代码将其从本地开发环境推送到集成、暂存和生产环境。

* 部署静态内容时&#x200B;**站点停机时间。**&#x200B;通常，静态内容是在[部署阶段](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase)部署的。 此过程可能需要长达30分钟或更长时间，这是业务所无法接受的。 配置管理将静态内容部署移动到[构建阶段](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase)，这不需要停机。

## 技术版本

* 用于配置管理的云基础架构&#x200B;**2.1.4**&#x200B;及更高版本上的Adobe Commerce
* 云基础架构&#x200B;**2.2**&#x200B;及更高版本上的Adobe Commerce，用于配置管理/管道部署

## 什么是配置管理

为了简单起见，配置管理（也称为Pipeline Deployment）过程将云基础架构实施（数据库）上的Adobe Commerce中的所有配置设置提取到单个PHP文件中。 然后，将文件添加到Git提交并在所有环境中推送该文件。

这提供了以下好处：

* **所有环境中一致的设置：**&#x200B;导出到配置文件的所有设置都将被锁定(Commerce管理员中的相应字段变为只读)，这确保在您跨所有环境推送文件时配置一致。
* **停机时间缩短：**&#x200B;静态文件部署从[部署阶段](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase)（要求站点处于维护模式）转移到[构建阶段](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase)（当站点未处于维护模式，并且在发生错误或问题时不会关闭）。
* 在Cloud Infrastructure 2.2及更高版本上使用Adobe Commerce的&#x200B;**受保护的敏感数据：**，该进程还会将任何敏感数据（例如，付款网关凭据）导出到`env.php`文件。 此文件只应保存到在其中创建它的环境，而不应通过Git分支进行推送。

我们强烈建议您在部署中应用配置管理方法。

## 配置管理（位于我们的开发人员文档中）

* 云基础架构上的&#x200B;*Adobe Commerce指南中的&#x200B;**2.1.X**&#x200B;[&#128279;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hans)和[示例](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hans)的配置管理*
* 云基础架构上的&#x200B;*Adobe Commerce指南中的&#x200B;**2.2.X**&#x200B;[&#128279;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hans)和[示例](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hans)的配置管理*
* [从&#x200B;*在云基础架构上升级Adobe Commerce*&#x200B;主题的2.0.X或2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=zh-Hans#upgrade-from-older-versions)部分升级
* *云基础架构上的Adobe Commerce配置指南*&#x200B;中的[管道部署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html?lang=zh-Hans) — 对于云基础架构上的Adobe Commerce，您无需遵循本指南中的说明。 内容仅供参考。 我们已在云基础架构上通过Adobe Commerce提供构建服务器、集成环境等。
