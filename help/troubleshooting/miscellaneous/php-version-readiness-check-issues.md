---
title: PHP版本准备情况检查问题
description: 本文介绍了在使用Web设置向导在本地安装/升级Adobe Commerce时可能遇到的PHP版本问题的解决方案。
exl-id: dee939cf-b9b2-4750-965c-5b8908a4498d
feature: Variables
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# PHP版本准备情况检查问题

本文介绍了在使用Web设置向导在本地安装/升级Adobe Commerce时可能遇到的PHP版本问题的解决方案。

>[!WARNING]
>
>在云基础架构上的Adobe Commerce上，请注意，如果没有48个工作小时的通知，服务升级就无法推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产环境的48小时之前 [提交支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) 详细描述所需的服务升级，并说明希望升级过程开始的时间。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* Magento Open Source2.2.x和2.3.x

## 不支持的PHP版本

### 问题

检查失败，因为您使用的是不支持的PHP版本。

### 解决方案

要解决此问题，请使用我们的开发人员文档中所列的受支持版本之一 [2.3.x系统要求](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html) 和 [2.2.x系统要求](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html).

## PHP就绪检查不显示

### 问题

PHP准备情况检查不会显示PHP版本，如下图所示。
![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)

### 解决方案

这是cron作业设置不正确的症状。 有关更多信息，请参阅 [设置cron作业](https://devdocs.magento.com/guides/v2.3/install-gde/install/post-install-config.html#post-install-cron) 在我们的开发人员文档中。

## PHP版本不正确

### 问题

该检查报告不正确的PHP版本。 通常，只有安装了多个PHP版本的高级用户才会发生这种情况。 在某些情况下，准备情况检查会失败；而在其他情况下，可能会通过。

如果准备情况检查报告的PHP版本不正确，则是PHP CLI和Web服务器插件之间的PHP版本不匹配的结果。 Adobe Commerce要求您使用 *一个版本* PHP的CLI（运行cron）和Web服务器(运行Commerce管理员、组件管理器和系统升级)。

### 解决方案

我们假定，如果您遇到此问题，您就是可能在系统上安装了多个PHP版本的高级用户。

要解决此问题，请尝试以下操作：

* 重新启动Web服务器或php-fm。
* 查看 `$PATH` PHP的多个路径的环境变量。
* 使用 `which php` 命令查找路径中的第一个PHP可执行文件；如果不正确，请将其删除或创建指向正确PHP版本的符号链接。
* 使用 [`phpinfo.php`](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/optional.html#install-optional-phpinfo) 页面以收集更多信息。
* 在我们的开发人员文档中，确保您根据我们的系统要求运行支持的PHP版本：
   * [Adobe Commerce 2.3.x系统要求](https://devdocs.magento.com/guides/v2.3/install-gde/system-requirements.html)
   * [Adobe Commerce 2.2.x系统要求](https://devdocs.magento.com/guides/v2.2/install-gde/system-requirements.html)
* 为PHP命令行和PHP Web服务器插件设置相同的PHP设置，如中所述 [PHP配置选项](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-centos-ubuntu.html) 在我们的开发人员文档中。
