---
title: “ACSD-55100： [!DNL GraphQL] 不会在搜索结果中返回超过10,000的产品”
description: 应用ACSD-55100修补程序以修复Adobe Commerce问题，该问题导致GraphQL在搜索结果中未返回超过*10k*的产品。
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 951e5cd4-9690-43df-9e51-deab73f9eb54
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-55100： [!DNL GraphQL]在搜索结果中未返回超过10,000的产品

ACSD-55100修补程序修复了以下问题：[!DNL GraphQL]不会返回搜索结果中超过&#x200B;*10k*&#x200B;的产品。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46时，此修补程序可用。 修补程序ID为ACSD-55100。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL GraphQL]不会返回搜索结果中超过&#x200B;*10k*&#x200B;的产品。

<u>先决条件</u>：

如果是&#x200B;**[!DNL OpenSearch]**，请确保您使用的是最新的可用版本。

为了解决报告的问题，引入了时间点功能，该功能在&#x200B;**[!DNL OpenSearch]** 2.5.0之后可用，并且需要`opensearch-project/opensearch-php`包的版本2.2。

但是，`magento/magento-cloud-metapackage`存在冲突，它指定了`opensearch-project/opensearch-php`程序包上的依赖项，该程序包应小于版本2.0.1。


此依赖项阻止将[opensearch-project/opensearch-php]包更新到最新版本2.2。

因此，系统遇到以下错误，并针对超过&#x200B;*10,000*&#x200B;的产品返回null结果。

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

现有依赖关系使得直接向`composer.json`文件添加版本并将`opensearch-project/opensearch-php`包更新到版本2.2变得困难。

要解决此问题，请在主`composer.json`文件中的require块下加入以下行。 之后，重新部署以将有问题的包更新到最新版本。

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>重现步骤</u>：

1. 生成包含&#x200B;*15k*&#x200B;产品的目录。
1. 发送[!DNL GraphQL]：

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>预期的结果</u>：

Total_count = *15k*
您应该能够显示所有产品。

<u>实际结果</u>：

Total_count = *10k*
您不能在*10k*&#x200B;批次之后再显示任何产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
