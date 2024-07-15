---
title: 'MDVA-36615：目录产品网格筛选器结果不正确'
description: MDVA-36615修补程序修复了管理产品网格中的产品计数不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21后，即可使用此修补程序。 修补程序ID为MDVA-36615。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 7ed70753-c637-4c13-8290-aa5e8a4d1b65
feature: Catalog Management, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# MDVA-36615：目录产品网格筛选器结果不正确

MDVA-36615修补程序修复了管理产品网格中的产品计数不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21时，此修补程序可用。 修补程序ID为MDVA-36615。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理产品网格中的产品计数不正确。

<u>要再现的步骤：</u>

1. 创建名称中具有相同短语的简单可配置产品（例如“red shirt”/“red shirt xs”）。
1. 在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**目录** > **产品** >搜索此短语。
1. 单击&#x200B;**筛选器**。 将类型设置为&#x200B;*可配置的产品*。
1. 单击&#x200B;**应用筛选器**。

<u>实际结果：</u>

匹配的产品计数器中的正确数字。

<u>预期结果：</u>

匹配的产品计数器中的数字不正确。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
