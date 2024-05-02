---
title: 'MDVA-37897：从“最近查看的项目”添加产品时重定向不正确'
description: MDVA-37897修补程序解决了当用户尝试使用最近查看的构件中的选项添加产品时，重定向不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-37897。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。
exl-id: f0a86e02-b357-4d2d-8386-e9cc045bcf06
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-37897：从“最近查看的项目”添加产品时重定向不正确

MDVA-37897修补程序解决了当用户尝试使用最近查看的构件中的选项添加产品时，重定向不正确的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.1。 修补程序ID为MDVA-37897。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户尝试从“最近查看”部分添加具有所需选项的产品时，用户被重定向到产品列表页面而不是产品详细信息页面。

<u>重现问题的步骤</u>：

1. 使用可自定义的选项（类型：单选按钮）创建简单产品。
1. 配置“最近查看的项目”小组件以显示产品。
1. 访问具有可自定义选项的产品，以便这些产品显示在“最近查看的项目”小组件中。
1. 单击 **添加到购物车** 位于最近查看的构件中的一个产品上。

<u>预期结果</u>：

您将被重定向到产品详细信息页面以选择相关选项。

<u>实际结果</u>：

您将被重定向到产品列表页面。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* Adobe Commerce在我们的云基础架构上： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Adobe Commerce质量修补程序的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) 部分。
