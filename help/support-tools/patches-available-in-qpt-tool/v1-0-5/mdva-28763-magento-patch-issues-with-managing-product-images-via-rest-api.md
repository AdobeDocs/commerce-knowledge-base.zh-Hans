---
title: 'MDVA-28763：通过REST API管理产品图像时出现问题'
description: MDVA-28763修补程序解决了与使用REST API管理媒体集相关的多个问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。 计划在更高的Adobe Commerce版本中修复这些问题。
exl-id: 736fbfa8-b6a3-413c-a220-fd772d87ed04
feature: REST, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-28763：通过REST API管理产品图像时出现问题

MDVA-28763修补程序解决了与使用REST API管理媒体集相关的多个问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5时，此修补程序可用。 计划在较新版本的Adobe Commerce中修复这些问题（请参阅[问题](#issues)中的问题描述）。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce内部部署2.3.2 - 2.3.3.x
* 云基础架构上的Adobe Commerce 2.3.2 - 2.3.3.x

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题 {#issues}

MDVA-28763修补程序修复了以下与介质集相关的问题：

* 使用REST API更新YouTube视频(`PUT rest/V1/products/ {SKU}`)时，Adobe Commerce会显示视频的缩略图，但单击“播放”按钮时视频播放器未加载。 计划在Adobe Commerce 2.3.6中修复。
* `PUT /V1/products/:sku/media/:entryId`调用将创建一个新条目，而不是替换现有条目。 已在Adobe Commerce 2.3.5中修复。
* 将产品分配给多个商店视图时，产品图像删除出现问题。 已在Adobe Commerce 2.3.4中修复。
* 现在，具有多个网站的商家可以使用REST创建和更新产品，同时保留图像和图像角色继承。 以前，当商家使用REST创建和更新产品，并为商店视图更新产品时，将为该商店视图加载并保存默认图像角色。 因此，存储视图图像角色在更新后停止从默认范围继承。 计划在Adobe Commerce 2.3.6中修复。
* 媒体属性（图像、缩略图、..） 存储视图中引用了已删除映像的值，这些映像未自动清理。 计划在Adobe Commerce 2.4.2中修复。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
