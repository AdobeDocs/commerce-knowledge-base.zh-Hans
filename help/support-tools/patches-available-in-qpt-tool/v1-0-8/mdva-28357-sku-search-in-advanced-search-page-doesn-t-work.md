---
title: 高级搜索页面中的MDVA-28357 SKU搜索不起作用
description: MDVA-28357解决了“高级搜索”页面中按产品SKU进行搜索时，搜索结果中不会显示相关产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.1中已修复此问题。
exl-id: a89409b0-3155-4fac-9842-0d129dacd6e1
feature: Search
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 高级搜索页面中的MDVA-28357 SKU搜索不起作用

MDVA-28357解决了“高级搜索”页面中按产品SKU进行搜索时，搜索结果中不会显示相关产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8时，此修补程序可用。 请注意，Adobe Commerce版本2.4.1中已修复此问题。

## 受影响的产品和版本

* 此补丁是为Adobe Commerce内部部署2.3.4-p2设计的。
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.0到2.3.5-p2以及2.4.0到2.4.0-p1上的Adobe Commerce。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在高级搜索中，使用SKU进行搜索时，会使用通配符查询SKU字段。 但是，通配符只能与`sku.keyword`一起使用，因此不会返回预期的产品。

<u>重现步骤</u>

1. 转到“高级搜索”页。
1. 按SKU编号搜索。

<u>实际结果</u>

显示错误消息： *我们找不到符合这些搜索条件的任何项目。 修改您的搜索*。

<u>预期的结果</u>

显示一个产品项并带有消息：使用以下搜索条件&#x200B;*找到了* 1项&#x200B;*SKU： XX-XXXX*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署：在开发人员文档中[使用Quality Patches Tool](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)应用修补程序。
* 云基础架构上的Adobe Commerce：在开发人员文档中，[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
