---
title: 'MDVA-38468：保存CMS页面时收到错误消息'
description: “MDVA-38468 Adobe Commerce修补程序修复了用户在保存CMS页面时收到错误消息：*具有相同ID“PAGE_ID”的项目已存在*的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26后，即可使用此修补程序。 修补程序ID为MDVA-38468。 请注意，Adobe Commerce 2.3.6中已修复此问题。'
exl-id: 7fe80308-50b7-4786-a43c-cce607eb606c
feature: CMS, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-38468：保存CMS页面时收到错误消息

MDVA-38468 Adobe Commerce修补程序修复了以下问题：在保存CMS页面时，用户收到错误消息：*具有相同ID“PAGE_ID”的项目已存在，*。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.26时，此修补程序可用。 修补程序ID为MDVA-38468。 请注意，Adobe Commerce 2.3.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
云基础架构上的Adobe Commerce 2.3.2-p2

**与Adobe Commerce版本兼容：**
Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.2-2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

尝试保存CMS页面时，您收到以下错误消息：*具有相同ID“PAGE_ID”的项目已存在。*

<u>重现步骤</u>：

1. 创建新网站+商店+商店回顾。
1. 再创建一个网站+商店+商店回顾。
1. 转到&#x200B;**内容** > **层次结构** >将任何现有的CMS页面添加到层次结构树。
1. 转到&#x200B;**内容** > **页面** > **添加新页面**：
   * 添加任何标题。
   * 在“网站中的页面”部分中，分配给两个已创建的审核。
   * 在“层次结构”部分中，分配给任何类别。
   * **保存并继续编辑**。

<u>预期的结果</u>：

保存页面时，不会出现任何错误。

<u>实际结果</u>：

页面已保存，但您收到以下错误消息：*具有相同ID“PAGE_ID”的项目(Magento\VersionsCms\Model\Hierarchy\Node)已存在。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
