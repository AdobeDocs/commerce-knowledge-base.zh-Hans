---
title: '''MDVA-35092： Vimeo错误：“找不到视频”'
description: 'MDVA-35092修补程序修复了您看到以下错误的问题：*“找不到视频”*。 当您使用Adobe Commerce产品管理员中的本机“添加视频”界面输入Vimeo视频时，会显示此错误消息。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.3中已修复此问题。'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092： Vimeo错误：“找不到视频”

MDVA-35092修补程序修复了您看到以下错误的问题：*“找不到视频”*。 当您使用Adobe Commerce产品管理员中的本机“添加视频”界面输入Vimeo视频时，会显示此错误消息。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17时，此修补程序可用。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.5 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

Vimeo简单API会停止按预期运行。

<u>重现步骤</u>：

1. 登录到管理员。
1. 若要编辑现有产品，请转到&#x200B;**目录** > **产品** > **编辑**，或者若要创建新产品，请转到&#x200B;**目录** > **产品** > **编辑** > **添加产品**。
1. 单击“产品”页面上的&#x200B;**图像和视频**&#x200B;选项卡。
1. 单击&#x200B;**添加视频**&#x200B;并添加Vimeo视频的URL。 单击&#x200B;**保存**。

<u>预期的结果</u>：

找到并保存新视频。

<u>实际结果</u>：

错误：显示&#x200B;*“找不到视频”*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
