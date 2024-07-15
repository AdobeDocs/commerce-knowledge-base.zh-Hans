---
title: “MDVA-34192修补程序：无法以特定格式修改客户日期”
description: MDVA-34192修补程序修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-34192修补程序：无法以特定格式修改客户日期

MDVA-34192修补程序修复了无法使用dd/mm/yyyy格式修改/指定客户出生日期的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.5-p1上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** 2.3.4-2.3.6

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

该补丁解决了若干问题。 以下是其中一个的描述和重现步骤。

当我们使用自定义日期属性进行筛选并且管理员用户区域设置为en\_GB时，产品网格筛选器无法正常工作。

<u>要再现的步骤：</u>：

1. 创建&#x200B;**界面区域设置**&#x200B;设置为&#x200B;*英语（英国）*&#x200B;的管理员用户。
1. 使用以下配置创建日期属性：
   * 商店所有者的&#x200B;**目录输入类型**： *日期*
   * **在筛选器选项中使用**： *是*
   * **添加到列选项**： *是*
1. 将属性分配给属性集。
1. 转到产品编辑页面，使用日期选取器为新属性选择日期并保存。
1. 尝试使用新的日期属性筛选产品网格。

<u>预期结果：</u>：

当管理员用户区域设置为en\_GB时，产品过滤器可正确用于自定义日期属性。

<u>实际结果：</u>：

当管理员用户区域设置为en\_GB时，产品过滤器无法正确用于自定义日期属性。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
