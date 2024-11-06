---
title: PHP版本准备情况检查问题
description: 本文介绍了在使用Web设置向导在本地安装/升级Adobe Commerce时可能遇到的PHP版本问题的解决方案。
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# PHP版本准备情况检查问题

本文介绍了在使用Web设置向导在本地安装/升级Adobe Commerce时可能遇到的PHP版本问题的解决方案。

>[!WARNING]
>
>在云基础架构上的Adobe Commerce上，请注意，如果没有48个工作小时的通知，服务升级就无法推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产前48小时[提交支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，其中详细列出所需的服务升级并指明希望升级过程开始的时间。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* Magento Open Source2.2.x和2.3.x

## 不支持的PHP版本

### 问题

检查失败，因为您使用的是不支持的PHP版本。

### 解决方案

要解决此问题，请使用我们的开发人员文档[2.3.x系统要求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)和[2.2.x系统要求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)中列出的受支持版本之一。

## PHP就绪检查不显示

### 问题

PHP准备情况检查不会显示PHP版本，如下图所示。
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### 解决方案

这是cron作业设置不正确的症状。 有关详细信息，请参阅我们的开发人员文档中的[设置cron作业](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration)。

## PHP版本不正确

### 问题

该检查报告不正确的PHP版本。 通常，只有安装了多个PHP版本的高级用户才会发生这种情况。 在某些情况下，准备情况检查会失败；而在其他情况下，可能会通过。

如果准备情况检查报告的PHP版本不正确，则是PHP CLI和Web服务器插件之间的PHP版本不匹配的结果。 Adobe Commerce要求您对CLI（运行cron）和Web服务器(运行Commerce管理、组件管理器和系统升级)都使用&#x200B;*一个版本的PHP*。

### 解决方案

我们假定，如果您遇到此问题，您就是可能在系统上安装了多个PHP版本的高级用户。

要解决此问题，请尝试以下操作：

* 重新启动Web服务器或php-fm。
* 检查`$PATH`环境变量，以查看指向PHP的多个路径。
* 使用`which php`命令查找路径中的第一个PHP可执行文件；如果不正确，请将其删除或创建指向正确PHP版本的符号链接。
* 使用[`phpinfo.php`](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software)页面收集更多信息。
* 在我们的开发人员文档中，确保您根据我们的系统要求运行支持的PHP版本：
   * [Adobe Commerce系统要求](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
* 为PHP命令行和PHP Web服务器插件设置相同的PHP设置，如开发人员文档中的[PHP配置选项](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#php-settings)中所述。
