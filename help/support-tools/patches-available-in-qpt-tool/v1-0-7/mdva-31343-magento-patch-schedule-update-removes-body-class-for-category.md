---
title: 'MDVA-31343修补程序：计划更新删除类别的主体类'
description: MDVA-31343修补程序修复了在计划更新期间删除为类别分配的布局正文CSS类的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 Adobe Commerce 2.4.2中计划修复此问题。
exl-id: 50dbff01-cb77-4cac-b90e-5c4b06f5e4e7
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-31343修补程序：计划更新删除类别的主体类

MDVA-31343修补程序修复了在计划更新期间删除为类别分配的布局正文CSS类的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 Adobe Commerce 2.4.2中计划修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.4 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

布局正文类在计划更新后从类别中删除。

<u>重现步骤</u>：

1. 在Commerce管理员中，创建一个类别。
1. 在&#x200B;**设计**&#x200B;分区中设置&#x200B;**布局** = *类别 — 全宽*。
1. 保存类别。
1. 转到类别前端页面。 在页面源中，注意

   ```css
   page-layout-category-full-width
   ```

   css类。
1. 在&#x200B;**目录** > **类别**&#x200B;下，在新类别的&#x200B;*计划更改*&#x200B;部分中单击&#x200B;**计划新更新**。
1. 等待计划更新开始，运行cron并刷新缓存。
1. 转到前端上的类别页面并检查页面源。

<u>预期的结果</u>：

在页面正文中，您会看到

```css
page-layout-category-full-width
```

css类。

<u>实际结果</u>：

在页面正文中，您会看到

```css
page-layout-2columns-left
```

CSS类，该类是类别页面的默认类。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
