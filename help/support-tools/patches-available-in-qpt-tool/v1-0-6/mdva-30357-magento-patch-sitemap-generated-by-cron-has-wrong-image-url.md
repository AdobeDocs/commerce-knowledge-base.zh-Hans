---
title: 'MDVA-30357：cron生成的Sitemap具有错误的图像URL'
description: MDVA-30357修补程序修复了Commerce管理员中cron生成的Sitemap创建的错误图像URL的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
feature: Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# MDVA-30357：cron生成的Sitemap具有错误的图像URL

MDVA-30357修补程序修复了Commerce管理员中cron生成的Sitemap创建的错误图像URL的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.3.2到2.4.0

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Adobe Commerce中cron生成的Sitemap包含错误的图像URL路径。

<u>重现步骤</u>：

1. 在“Commerce管理员”中，创建新网站、商店或商店视图。
1. 向每个商店至少添加一个产品，并向每个产品至少添加一个图像。
1. 在&#x200B;**管理员** > **商店** > **配置** > **目录** > **XML Sitemap** > **生成设置**&#x200B;中启用按计划&#x200B;**生成** Sitemap。
1. 在&#x200B;**管理员** > **营销** > **站点地图**&#x200B;中，使用站点地图名称（如“*站点地图.xml*”）手动为两个商店中的任意商店生成站点地图。
   * 将文件重命名为类似“*manual\_sitemap.xml*”的文件，或者将文件内容复制到任何文本编辑器。
1. 通过cron作业`sitemap_generate`生成相同的Sitemap。
1. 比较手动生成的站点地图“*manual\_sitemap.xml*”和cron“*sitemap.xml*”生成的站点地图。

<u>预期的结果</u>：

缓存的站点地图图像路径URL正确。

<u>实际结果</u>：

cron生成的站点地图包含错误的图像路径URL。 如果尝试从“*sitemap.xml*”打开图像，将显示默认占位符。 手动生成的站点地图URL不受此问题的影响。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。

要了解有关站点应用程序的更多信息，请参阅我们的开发人员文档中的以下文章：

* [添加Sitemap和搜索引擎机器人](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [配置并运行cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [在浏览器中运行的安全cron.php](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)
