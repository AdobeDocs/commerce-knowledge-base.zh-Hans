---
title: Adobe Commerce中的产品Recommendations模块疑难解答
description: 本文讨论对的故障排除建议
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: b20ad74194bacb09116131f4a8da1006da75738a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Adobe Commerce中的产品Recommendations模块疑难解答

本文讨论对的故障排除建议

```php
magento/product-recommendations
```

模块及其依赖关系

```php
saas-export
```

模块，因为要使用Adobe Commerce中的产品Recommendations工具，您需要两个模块都运行。

## 受影响的产品和版本

* Adobe Commerce 2.4.4 - 2.4.7

## 产品推荐模块疑难解答

如果您已配置

```php
magento/product-recommendations
```

模块正确(请查看我们的开发人员文档中的[产品Recommendations — 安装和配置Recommendations](https://devdocs.magento.com/recommendations/install-configure.html)。)，但是您没有看到任何推荐，请尝试以下操作：

* 模块可能没有足够的时间来收集行为数据。 允许系统运行24小时，以便可以开始收集数据。 可以考虑部署不需要任何行为数据的推荐类型，例如“更多与此类似的内容”。

* 如果您未看到配置的推荐，则可能还没有足够的数据来为用户构建推荐。

* 请确保SaaS数据空间或API密钥有效。 如果在产品推荐初始化过程中指定SaaS数据空间或API密钥后出现错误，请检查以确保您正确输入了[SaaS数据空间和API密钥](https://docs.magento.com/user-guide/configuration/services/saas.html)（在我们的用户指南中）。 要确保MageID和API密钥相关联，拥有MageID的用户(通常是拥有Adobe Commerce许可证的用户)必须是生成API密钥的同一用户。 如果必须更改已使用的MageID，请[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

>[!NOTE]
>
>如果启用了[Cookie限制模式](https://docs.magento.com/m2/ce/user_guide/stores/compliance-cookie-restriction-mode.html)（在我们的用户指南中），则在购物者同意之前，Adobe Commerce不会收集行为数据。 如果“Cookie限制模式”被禁用，Adobe Commerce会默认收集行为数据。

## 目录SaaS导出模块

有关目录SaaS导出的问题(

```php
saas-export
```

)模块：

1. 确认[cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html)（在我们的开发人员文档中）作业正在运行。
1. 确认[索引器](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)（在我们的开发人员文档中）正在运行，并且    ```php    Product Feed    ```    索引器设置为    ```php    Update by Schedule    ```    .
1. 确认模块已启用。 此    ```php    saas-export    ```    metapackage安装以下模块，必须启用所有这些模块：    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. 查看[日志](https://devdocs.magento.com/guides/v2.3/config-guide/cli/logging.html)（在我们的开发人员文档中）。 确保没有与上述模块相关的错误。
1. 刷新配置缓存。 转到&#x200B;**系统** > **工具** > **缓存管理**，并清除配置缓存。
1. 确认中存在数据    ```php    catalog_data_exporter_products    ```    数据库表。

## 活动

在我们的开发人员文档中，[推荐事件](https://devdocs.magento.com/recommendations/verify.html)描述了发送到Adobe Commerce的行为事件。

## 相关阅读

* [产品Recommendations — 概述](https://devdocs.magento.com/recommendations/product-recs.html)（位于我们的开发人员文档中）
* [产品Recommendations — 在我们的开发人员文档中安装和配置Recommendations](https://devdocs.magento.com/recommendations/install-configure.html)
* 我们用户指南中的[营销 — 产品Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/product-recommendations.html)
* 在我们的用户指南中[创建产品Recommendations](https://docs.magento.com/m2/ee/user_guide/marketing/create-new-rec.html)
