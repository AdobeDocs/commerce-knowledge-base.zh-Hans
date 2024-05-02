---
title: 'MDVA-33894修补程序：适用于快速订购的捆绑包解决方案'
description: MDVA-33894修补程序修复了快速订购功能的多个问题，包括添加和删除多个产品以及SKU区分大小写。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: d0b18e71-5f48-441e-a8b9-c459f3d34599
feature: Cache, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-33894修补程序：适用于快速订购的捆绑包解决方案

MDVA-33894修补程序修复了快速订购功能的多个问题，包括添加和删除多个产品以及SKU区分大小写。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 已安装1.0.15。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：** 云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.4.0-2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

MDVA-33894修补程序是一个捆绑解决方案，修复了以下问题：

* **我的帐户** > **按SKU排序** 功能区分大小写：如果您输入有效的SKU，但大小写不正确（大写而不是小写等），则Adobe Commerce会引发错误。
* 当购物者使用快速订购将多个产品添加到其购物车并尝试删除产品时，产品未被删除。
* 将多个SKU添加到批量订单时出现区分大小写问题。
* 之前输入的SKU存在快速订购页面缓存问题。
* 快速订购数量未反映在购物车中。
* 未正确验证SKU复制。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT工具中可用的其他修补程序的信息，请参阅 [QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
