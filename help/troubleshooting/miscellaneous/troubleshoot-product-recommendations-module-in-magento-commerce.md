---
title: Adobe Commerce中的[!UICONTROL Product Recommendations]模块疑难解答
description: 本文介绍Adobe Commerce中[!UICONTROL Product Recommendations]模块的故障排除建议。
exl-id: 431ee31e-eb5b-400c-9c99-cc86613453d7
feature: Cache, Compliance, Extensions, Marketing Tools, Personalization, Products, Recommendations
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Adobe Commerce中的[!UICONTROL Product Recommendations]模块疑难解答

本文讨论对的故障排除建议

```php
magento/product-recommendations
```

模块及其依赖关系

```php
saas-export
```

模块，因为您需要两个模块都运行才能在Adobe Commerce中使用[!UICONTROL Product Recommendations]工具。

## 受影响的产品和版本

* Adobe Commerce 2.4.4 - 2.4.7

## 产品推荐模块疑难解答

如果您已配置

```php
magento/product-recommendations
```

模块正确，（请查看我们的开发人员文档中的[[!UICONTROL Product Recommendations - Install and Configure]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure)。）但是您没有看到任何推荐，请尝试以下操作：

* 模块可能没有足够的时间收集行为数据。 允许系统运行24小时，以便可以开始收集数据。 考虑部署不需要任何行为数据的推荐类型，例如&quot;*更多与此类似的数据*&quot;。

* 如果您未看到配置的推荐，则可能还没有足够的数据来为用户构建推荐。

* 确保[!DNL SaaS]数据空间或[!DNL API]键有效。 如果在产品推荐初始化过程中指定您的[!DNL SaaS]数据空间或[!DNL API]密钥后出现错误，请检查以确保您正确输入了[[!DNL SaaS] 数据空间和 [!DNL API] 密钥](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)（在我们的用户指南中）。 为确保关联[!DNL MageID]和[!DNL API]密钥，拥有[!DNL MageID]的用户(通常是Adobe Commerce许可证的所有者)必须是生成[!DNL API]密钥的同一用户。 如果必须更改已使用的[!DNL MageID]，请[提交支持票证](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)。

>[!NOTE]
>
>如果&#x200B;[**[!UICONTROL Cookie Restriction Mode]**](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law)（在我们的用户指南中）为&#x200B;*已启用*，则在购物者同意之前，Adobe Commerce不会收集行为数据。 如果&#x200B;**[!UICONTROL Cookie Restriction Mode]**被&#x200B;*禁用*，Adobe Commerce将默认收集行为数据。

## 目录[!DNL SaaS]导出模块

对于与目录[!DNL SaaS]导出相关的问题(

```php
saas-export
```

)模块：

1. 确认[[!DNL cron]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) （在开发人员文档中）作业正在运行。
1. 确认[[!UICONTROL indexers]](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)（在我们的开发人员文档中）正在运行，并且    ```php    Product Feed    ```    [!UICONTROL indexer]设置为    ```php    Update by Schedule    ```    .
1. 确认模块已启用&#x200B;**。 此    ```php    saas-export    ```    metapackage安装以下模块，所有这些模块都必须启用&#x200B;**：    ```php    "magento/module-catalog-data-exporter"      "magento/module-catalog-inventory-data-exporter"      "magento/module-catalog-url-rewrite-data-exporter"      "magento/module-configurable-product-data-exporter"      "magento/module-data-exporter"      "magento/module-saas-catalog"    ```
1. 查看[日志](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/enable-logging)（在我们的开发人员文档中）。 确保没有与上述模块相关的错误。
1. 刷新[!UICONTROL Configuration cache]。 转到&#x200B;**系统** > **工具** > **缓存管理**，然后清除[!UICONTROL Configuration cache]。
1. 确认`cde_products_products_feed`数据库表中存在数据。

   >[!NOTE]
   >
   >如果找不到该表，请检查`catalog_data_exporter_products`表。 在[!DNL Data Export]版本103.3.0版本中更改了表名称。

## 活动

[在我们的开发人员文档中验证事件集合](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/verify)描述了发送到Adobe Commerce的行为事件。

## 相关阅读

* 开发人员文档中的[产品推荐管理员开发](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
* 产品推荐指南中的[产品推荐简介](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)
* 在产品推荐指南中[创建产品推荐](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/admin/create)
* 在[数据导出指南中](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/troubleshooting-logging)查看日志并排除故障[!DNL SaaS]
* Adobe Commerce Data Export Guide for [[!DNL SaaS] 服务中的](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/saas-data-export/release-notes)数据导出扩展发行说明[!DNL SaaS]
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

