---
title: 'MDVA-36853：从大型媒体集未加载图像'
description: MDVA-36853修补程序修复了没有加载图像的问题，因为当您具有大型媒体目录时，页面生成器媒体集构件无法加载。
exl-id: 64e089d9-d443-4aa7-8e04-a3598b05958d
feature: CMS, Cache, Media
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# MDVA-36853：从大型媒体集中不加载图像

MDVA-36853修补程序修复了没有加载图像的问题，因为当您具有大型媒体目录时，页面生成器媒体集构件无法加载。

安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22时，此修补程序可用。 修补程序ID为MDVA-36853。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**在Cloud Infrastructure 2.4.2上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 在&#x200B;**管理员>商店>配置>高级>系统>媒体集**&#x200B;中设置&#x200B;**启用旧媒体集** = *是*。
1. 导航到&#x200B;**内容>块**，然后创建新的CMS块或编辑现有的CMS块。
1. 单击&#x200B;**使用Pagebuilder编辑**&#x200B;按钮。
1. 添加媒体元素。
1. 单击&#x200B;**从图库中选择**&#x200B;按钮。

<u>预期的结果</u>：

媒体集小部件和媒体集图像都会按预期加载。

<u>实际结果</u>：

当具有大的`pub/media/catalog/product/cache/`目录时，无法加载媒体集小部件和媒体集图像。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
