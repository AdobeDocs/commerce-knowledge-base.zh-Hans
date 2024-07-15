---
title: 'MDVA-36718：更改API后自定义选项仍保留'
description: MDVA-36718Magento修补程序修复了在通过API更改旧自定义选项后保留旧自定义选项的问题。
exl-id: e9755764-e563-4921-af75-a90e06237053
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# MDVA-36718：更改API后自定义选项仍保留

MDVA-36718Magento修补程序修复了在通过API更改旧自定义选项后保留旧自定义选项的问题。

安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22时，此修补程序可用。 修补程序ID为MDVA-36718。 请注意，该问题计划在Magento版本2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.1

**与Magento版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 添加&#x200B;**下拉类型**&#x200B;自定义选项。
1. 通过API更新自定义选项：将`PUT`请求发送到`/V1/products/options/{optionId}`。

<u>预期的结果</u>：

自定义选项会按预期更新。

<u>实际结果</u>：

添加了新自定义选项，但保留了旧自定义选项。

## 应用修补程序

要应用单个修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [检查我们的支持知识库中有关Quality Patches Tool的Magento问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
