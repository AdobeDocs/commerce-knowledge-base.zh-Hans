---
title: 'ACSD-48587：产品小部件不适用于包含HTML字符的SKU'
description: 应用ACSD-48587补丁以修复Adobe Commerce问题，该问题导致在产品构件匹配规则中HTML特殊字符无法显示匹配产品。
exl-id: 9f8f436c-f3ef-4510-a941-12f701e7524e
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48587：产品小部件不适用于包含HTML字符的SKU

ACSD-48587修补程序修复了以下问题：在产品构件匹配规则中HTML特殊字符会阻止它们显示匹配产品。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-48587。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品小组件无法使用包含&#x200B;*&amp;“*”符号的SKU。

<u>重现步骤</u>：

1. 在SKU中创建包含&#x200B;*&amp;&quot;*&#x200B;的产品（例如，s000&amp;01）。
1. 在&#x200B;*页面生成器*&#x200B;上编辑CMS页面的内容。
1. 添加产品小组件。
1. 编辑构件并将&#x200B;**[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**&#x200B;设置为。
1. 在产品SKU字段中输入包含&#x200B;*&amp;*&#x200B;的SKU。
1. 保存内容和CMS页面。
1. 检查&#x200B;*CMS页面*&#x200B;内容以了解&#x200B;*页面生成器预览*&#x200B;和产品店面。

<u>预期的结果</u>：

SKU中具有&#x200B;*&amp;“*”的产品显示在页面生成器预览和店面中。

<u>实际结果</u>：

SKU中具有&#x200B;*&amp;“*”的产品未显示在页面生成器预览中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
