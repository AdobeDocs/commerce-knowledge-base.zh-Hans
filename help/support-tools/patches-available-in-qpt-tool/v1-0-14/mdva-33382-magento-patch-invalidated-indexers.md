---
title: 'MDVA-33382修补程序：失效的索引器'
description: MDVA-33382修补程序解决了在类别中添加、删除或重新订购产品后索引器失效的问题。 失效的索引器为“catalog_category_product”、“catalogsearch_fulltext”（及其依赖项）。
exl-id: b4ac10ee-0f9d-4d7a-be72-c4d90ebadb10
feature: Catalog Management, Categories, Price Indexer
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# MDVA-33382修补程序：失效的索引器

MDVA-33382修补程序解决了在类别中添加、删除或重新订购产品后索引器失效的问题。 失效的索引器是`catalog_category_product`、`catalogsearch_fulltext`（及其依赖项）。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14时，此修补程序可用。 请注意，此问题将在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.4-p2上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 将所有索引索引器模式设置为&#x200B;**按计划**&#x200B;更新。
1. 从类别编辑页面中删除产品。
1. 保存类别。
1. 验证后端或CLI中的索引状态。

<u>预期的结果</u>：

以下索引未按预期失效： `catalog_category_product`、`catalogsearch_fulltext`（及其依赖项）。

<u>实际结果</u>：

以下索引已失效： `catalog_category_product`、`catalogsearch_fulltext`（及其依赖项）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
