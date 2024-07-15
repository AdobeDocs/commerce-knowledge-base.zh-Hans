---
title: 常规自定义模块故障诊断帮助
description: 本文介绍了可帮助对Adobe Commerce中的自定义模块进行故障排除的常规工具。
exl-id: c6603a2b-dc98-4022-ab29-c081c2b07415
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# 常规自定义模块故障诊断帮助

本文介绍了可帮助对Adobe Commerce中的自定义模块进行故障排除的常规工具。

## 问题

如果您意识到自定义模块中的功能存在问题，并且您没有收到明确指示该问题的错误消息，那么您将需要查阅实例的日志。

## 解决方案

检查日志，查看错误中是否存在具有自定义模块名称的条目。  根据所涉及的错误，解决方案可能会自行显示，或者如果您要打开[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，可能需要包含有用的Adobe Commerce日志信息。 有关日志的位置和可能解决方案的信息，请参阅以下段落。

### Adobe Commerce（所有部署方法）、Magento Open Source，所有2.X版本

1. 日志位置：
   * 云基础架构上的[Adobe Commerce我们的支持知识库中的入门计划架构日志](/help/how-to/general/log-locations-directories-for-starter-plan.md)。
   * [云基础架构上的Adobe Commerce Pro计划支持知识库中的架构日志](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)。
1. 根据您发现的错误，如果要启用、禁用或卸载自定义模块，这些文章将详细介绍这些操作：
   * 在开发人员文档中[启用或禁用模块](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-enable.html)。
   * 在开发人员文档中[卸载模块](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-uninstall-mods.html)。

### 云基础架构上的Adobe Commerce，所有版本

1. 在开发人员文档中记录位置： [云基础架构上的Adobe Commerce ](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)。
1. 根据您发现的错误，如果您希望启用、禁用或卸载自定义模块，我们开发人员文档中的以下文章将详细介绍这些操作：
   * [安装、管理和升级扩展](https://devdocs.magento.com/guides/v2.3/cloud/howtos/install-components.html)。
   * [组件部署失败](https://devdocs.magento.com/guides/v2.3/cloud/trouble/trouble_comp-deploy-fail.html)。

## 相关阅读

在我们的开发人员文档中：

* [模块概述](https://devdocs.magento.com/guides/v2.3/architecture/archi_perspectives/components/modules/mod_intro.html)
* [安装可选示例数据时出错](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_sample-data.html)
* [异常处理](https://devdocs.magento.com/guides/v2.3/graphql/develop/exceptions.html)
* 安装期间出现[异常](https://devdocs.magento.com/guides/v2.3/install-gde/trouble/tshoot_exceptions.html)
* [运行模块管理器](https://devdocs.magento.com/guides/v2.3/comp-mgr/module-man/compman-checklist.html)
* [模块配置文件](https://devdocs.magento.com/guides/v2.3/config-guide/config/config-files.html)
* [内存不足错误](https://devdocs.magento.com/guides/v2.3/comp-mgr/trouble/cman/out-of-memory.html)
