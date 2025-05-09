---
title: 'ACSD-46703：产品自定义项拖放不起作用'
description: 本文为产品可自定义选项拖放无法按预期工作的问题提供了解决方案。
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703：产品自定义项拖放不起作用

ACSD-46703修补程序修复了产品可自定义选项（拖放）无法按预期工作的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-46703。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[Quality Patches Tool]版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法将可自定义选项从一个页面拖放到另一个页面。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 将可自定义的选项添加到简单产品中，并确保添加20多个选项以实现分页。
1. 尝试在同一页面中移动可自定义的选项（拖放）。
1. 现在，尝试将可自定义选项从第二页移动到第一页。

<u>预期的结果</u>：

* 您可以将可自定义的选项从一个页面拖放到另一个页面。
* 您可以使用拖放功能对值进行排序，即使对于多个页面也是如此。

<u>实际结果</u>：

您无法使用拖放功能将任何值移动到其他页面。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或本地Magento Open Source： Quality Patches Tool指南中的[Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=zh-Hans)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅Quality Patches Tool指南中的[[!DNL Quality Patches Tool]： Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
