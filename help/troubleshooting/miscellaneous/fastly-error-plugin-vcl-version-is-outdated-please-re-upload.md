---
title: 'Fastly错误：插件VCL版本已过时！ 请重新上传'
description: 当您看到消息“*Plugin VCL版本已过时”时，本文会为您提供解决方案！ 请重新上传。*”在Commerce管理员的Fastly配置中，由于未安装最新的Fastly模块。
exl-id: d7870e9e-ba6b-49c2-a80c-26fb464cbae3
feature: Best Practices, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 快速错误：插件VCL版本已过时！ 请重新上传

本文提供了当您看到消息“*插件VCL版本已过时”时的解决方案！ 请重新上传。由于未安装最新的Fastly模块，在Commerce管理员的Fastly配置中出现“*”。

## 受影响的产品和版本

云基础架构2.2.x.、2.3.x<br>上的Adobe Commerce
Fastly：此错误可能会影响Fastly模块的所有版本，但最新版本除外。 有关最新版本的信息，请参阅GitHub上的[Fastly发行说明](https://github.com/fastly/fastly-magento2/releases)。

## 问题

1. 登录到Commerce管理面板。
1. 导航到&#x200B;**商店** > **配置** > **高级** > **系统** > **全页缓存**   **快速缓存。**
1. 在&#x200B;**自动上载和服务激活**&#x200B;部分中，将有“*插件VCL版本已过期！” 请重新上传。“*”通知。
1. 您尝试通过单击“上传VCL到Fastly”按钮来上传VCL代码片段，但您仍然看到警告“*插件VCL版本已过期！” 请重新上传。*”

## 原因

Fastly扩展已更新（以及捆绑的VCL配置和模板），但更新的VCL配置尚未上载到Fastly服务。 更新Adobe Commerce模块`Fastly_Cdn`时，必须再次将更新的VCL配置上传到Fastly。

## 解决方案

1. 检查是否已安装最新的ECE-Tools，以及我们的开发人员文档中的[当前版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html)。 ECE-Tools在其依赖项中有一个版本的Fastly包。

   这可能不是Fastly插件的最新版本，但可能是比您当前安装的版本更新的版本，最佳做法是安装最新的ECE工具。

1. 如果您不在当前版本的ECE-Tools上，请按照我们的开发人员文档中的以下步骤[升级](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)。
1. 升级ECE-Tools后，检查您现在是否安装了[Fastly插件](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets)的最新版本。
1. 如果Fastly插件不是当前版本，请按照以下步骤在开发人员文档中将插件[升级到最新版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#upgrade-the-fastly-module)。

## 相关阅读

* 有关设置和配置Fastly的信息，请参阅我们的开发人员文档中的[配置Fastly服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)。
* 有关Fastly的一般信息，请参阅[fastly.com](https://www.fastly.com/)。
