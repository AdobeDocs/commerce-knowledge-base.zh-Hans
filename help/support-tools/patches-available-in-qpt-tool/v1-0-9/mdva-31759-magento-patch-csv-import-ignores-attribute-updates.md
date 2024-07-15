---
title: 'MDVA-31759修补程序：CSV导入会忽略属性更新'
description: MDVA-31759修补程序修复了CSV导入会忽略具有*下拉列表*和*文本区域*类型的其他属性的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 5426866c-893f-4abe-bfbc-6e7b30dd8dab
feature: Attributes, Data Import/Export
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-31759修补程序： CSV导入会忽略属性更新

MDVA-31759修补程序修复了CSV导入忽略具有&#x200B;*下拉列表*&#x200B;和&#x200B;*文本区域*&#x200B;类型的其他属性的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

CSV导入忽略具有&#x200B;*下拉列表*&#x200B;和&#x200B;*文本区域*&#x200B;类型的其他属性。

<u>重现步骤</u>：

1. 登录到Commerce管理员。
1. 使用以下配置创建产品属性：
   * **默认标签**： *G003*
   * **商店所有者的目录输入类型**：*文本区域*&#x200B;或&#x200B;*下拉列表*
   * **属性代码**： *G003*
   * **作用域**： *全局*
1. 将以上属性添加到默认属性集。
1. 使用默认属性集创建产品，并指定新属性的值。
1. 将产品导出到CSV。
1. 更新&#x200B;**additional\_attributes**&#x200B;列中的属性值。
1. 导入更新的CSV。

<u>预期的结果</u>：

G003属性值已更新。

<u>实际结果</u>：

G003属性值不会更新。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
