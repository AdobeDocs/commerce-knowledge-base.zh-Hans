---
title: 将主题重置为默认值
description: 根据在自定义主题和开发商店时可能遇到的问题，您可能无权通过Commerce管理员进行访问。 您可以清除并重置为主题默认值，而无需访问管理员。 清除主题后，将应用默认Luma主题。
exl-id: 86304dd5-f448-4dcc-ad07-04ecc6c85b6d
feature: Cache
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 将主题重置为默认值

根据在自定义主题和开发商店时可能遇到的问题，您可能无权通过Commerce管理员进行访问。 您可以清除并重置为主题默认值，而无需访问管理员。 清除主题后，将应用默认Luma主题。

在您开发Adobe Commerce（所有部署）和Magento Open Source组件（模块、主题和语言包）时，快速变化的环境要求您定期清除某些目录和缓存。 否则，您的代码会在出现异常时运行，并且将无法正常运行。 有关详细信息，请参阅我们的开发人员文档中的[在开发过程中清除目录](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html)。

## 环境和技术

* Adobe Commerce内部部署
* 云基础架构上的Adobe Commerce
* Magento Open Source

## 先决条件

* 数据库工具

## 步骤

如果需要重置商店主题，但无法访问“管理员”面板，可以通过执行以下操作在数据库中重置商店主题：

1. 使用数据库工具（如[phpMyAdmin](https://devdocs.magento.com/guides/v2.2/install-gde/prereq/optional.html#install-optional-phpmyadmin)）或从命令行手动访问数据库以执行以下SQL查询： `UPDATE core_config_data SET value=NULL WHERE path='design/theme/theme_id'`
1. 清除以下目录：
   * `pub/static/frontend`
   * `var/view_preprocessing`
   * `var/cache`
   * `var/page_cache`

这样在商店视图级别上就不会设置主题，当您重新加载商店主页时，将应用默认的Luma主题。

## 其他信息

* 在开发人员文档中[在开发过程中清除目录](https://devdocs.magento.com/guides/v2.2/howdoi/php/php_clear-dirs.html)
