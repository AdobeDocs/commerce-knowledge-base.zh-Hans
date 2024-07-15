---
title: 'MDVA-31307：某些类别的内存不足'
description: MDVA-31307修补程序修复了“Magento\_Csp/模型/块缓存”占用大量内存并生成大量缓存字符串的问题，如果某些页面具有大量动态列入白名单的脚本和样式，则会导致出现问题。 提供的修补程序将优化此过程。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-31307。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 15d82f5b-bd43-4a0a-b756-d109dac6d2cd
feature: Cache, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-31307：某些类别的内存不足

MDVA-31307修补程序修复了`Magento\_Csp/Model/BlockCache`占用大量内存并生成大量缓存字符串的问题，该问题会导致某些页面出现问题，其中有许多动态列入白名单的脚本和样式。 提供的修补程序将优化此过程。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-31307。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Cloud Infrastructure 2.4.0上的Adobe Commerce版本** Adobe Commerce创建的

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了由于缓存块的动态CSP白名单问题而导致某些类别出现&#x200B;*内存不足*&#x200B;错误的问题。

<u>要再现的步骤：</u>

1. 生成小型配置文件夹具(`bin/magento setup:performance:generate-fixtures`)。
1. 在不同选项卡中打开所有类别页面。

<u>实际结果：</u>

*[日期和时间] PHP严重错误：未知行0中已耗用了1073741824字节的允许内存大小(尝试分配90112字节)
[日期和时间] PHP严重错误： /app/`<project-id>`/vendor/magento/module-csp/Model/Collector/DynamicCollector.php第31*&#x200B;行中允许的内存大小已用尽1073741824字节(尝试分配33554440字节)

<u>预期结果：</u>

所有页面均已正确打开。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
