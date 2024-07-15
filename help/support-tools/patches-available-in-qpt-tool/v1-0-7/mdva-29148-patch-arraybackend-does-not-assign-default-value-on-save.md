---
title: 'MDVA-29148： ArrayBackend在保存时未分配默认值'
description: MDVA-29148修补程序解决了“\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend”在保存时未分配默认值的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148：ArrayBackend在保存时未分配默认值

MDVA-29148修补程序解决了`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend`在保存时未分配默认值的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.3-p1.

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法）>=2.3.0 &lt;2.4.2。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过导入脚本或REST API创建产品时，使用`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend`后端模型并具有默认值的属性不会分配默认值。

<u>重现步骤</u>：

1. 创建使用`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend`后端模型和非空默认值的新全局属性。
1. 使用REST API创建新产品。
1. 从REST API获取该新产品，并确认该属性的自定义属性中不存在。

<u>预期的结果</u>：

自定义属性的默认值已保存到产品属性中。

<u>实际结果</u>：

自定义属性默认值未保存到产品属性。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
