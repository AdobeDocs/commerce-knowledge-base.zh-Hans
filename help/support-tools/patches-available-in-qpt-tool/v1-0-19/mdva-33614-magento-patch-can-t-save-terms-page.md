---
title: “MDVA-33614修补程序：无法保存术语页面”
description: 'MDVA-33614修补程序修复了无法保存对术语页面的编辑内容的问题，因为页面生成器会引发以下错误： *启动页面生成器时出错。 请咨询您的技术支持联系人*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-33614。 请注意，Adobe Commerce 2.4.2中已修复此问题。'
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# MDVA-33614修补程序：无法保存术语页面

MDVA-33614修补程序修复了无法将编辑内容保存到术语页面的问题，因为页面生成器会引发以下错误： *启动页面生成器时出错。 请咨询技术支持联系人*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-33614。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**在Cloud Infrastructure 2.4.1上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法保存对术语页面的编辑，因为页面生成器会引发错误。

<u>重现步骤</u>：

1. 在Commerce Admin中，转到&#x200B;**CONTENT** >元素> **页面**。
1. 选择“术语”页面。
1. 单击&#x200B;**编辑**。
1. 进行编辑并单击&#x200B;**保存**。

<u>预期的结果</u>：

保存页面时没有出现错误。

<u>实际结果</u>：

显示以下错误： *启动页面生成器时出错。 请咨询技术支持联系人*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
