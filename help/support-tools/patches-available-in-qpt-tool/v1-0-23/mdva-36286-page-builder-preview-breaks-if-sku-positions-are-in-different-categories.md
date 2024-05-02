---
title: 'MDVA-36286：如果SKU职位位于不同类别，则页面生成器预览会中断'
description: MDVA-36286修补程序解决了当同一SKU在子类别中具有不同位置时，页面生成器产品小组件预览中断的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.23后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: 0f7d2506-569a-4b70-82bf-0f153014c48a
feature: CMS, Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-36286：如果SKU职位位于不同的类别中，则页面生成器预览会中断

MDVA-36286修补程序解决了当同一SKU在子类别中具有不同位置时，页面生成器产品小组件预览中断的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.23。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.6 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤：</u>

1. 创建包含几个产品的类别。
   ![products_magento_ordered.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_ordered.png)
1. 创建一个子类别，该子类别具有相同的产品，但职位不同。
   ![products_magento_different_position.png](/help/support-tools/patches-available-in-qpt-tool/assets/products_magento_different_position.png)
1. 编辑CMS页面内容以通过页面生成器添加产品小部件。 （选择上面的父类别）。
   ![cms_page_magento.png](/help/support-tools/patches-available-in-qpt-tool/assets/cms_page_magento.png)
1. 保存并等待内容预览。

<u>预期结果：</u>

内容预览显示产品小组件。

<u>实际结果：</u>

错误显示：

*很抱歉，生成此内容时出错。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
