---
title: 修订的Google修补程序所有Adobe Commerce版本上的访问丢失
description: '本文为Adobe Commerce商家提供了与3.54+的任何最新 [!DNL Google Maps] 版本都不兼容的修复。'
feature: Install, Upgrade
role: Developer
source-git-commit: cf235c2fdd7a36d7e3b126de35c51e6711cd3845
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 修订了所有Adobe Commerce版本上[!DNL Google Maps]访问丢失的修补程序

本文修复了与3.54+版本的任何最新[!DNL Google Maps]版本不兼容的Adobe Commerce商家。 此修复是为了解决Adobe Commerce商家无法再访问任何版本的Adobe Commerce中的[!DNL Google Maps]的问题。

## 受影响的版本和产品

* Adobe Commerce和/或其他所用技术的版本。
* 云和本地版本上的Adobe Commerce *2.4.4* - *2.4.7*。

## 问题

在&#x200B;*2024年6月14日* [!DNL Google Maps]版本&#x200B;*3.53*&#x200B;到达生命周期结束并被关闭[!DNL Google]。

有关详细信息，请参阅[[!DNL Google Maps Platform: Maps JavaScript API]](https://developers.google.com/maps/documentation/javascript/versions#documentation-for-the-api-versions)。

Adobe Commerce与3.54及更高版本的任何最新[!DNL &#x200B; Google Maps]版本不兼容。

不兼容是由旧版`prototype.js script`导致的，该旧版通过`lib/web/legacy-build.min.js`加载将覆盖本机Array.from函数，从而导致与[!DNL &#x200B; Google Maps] API直接冲突。

请参阅[[!DNL Google Maps: JS Best Practices]](https://developers.google.com/maps/documentation/javascript/best-practices)。

<u>重现问题的步骤</u> ：

1. 单击&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Pages]** >并选择&#x200B;**[!UICONTROL New Page]**。
1. 展开内容块并单击编辑&#x200B;**[!DNL PageBuilder]**&#x200B;按钮。
1. 将“映射内容块”从&#x200B;**[!DNL PageBuilder]**&#x200B;菜单拖动到页面。

<u>预期结果：</u>

[!DNL Google Maps]应按预期工作。

<u>实际结果：</u>

将“映射内容块”从&#x200B;**[!DNL PageBuilder]**&#x200B;菜单拖放到页面时，出现错误消息，如&#x200B;*“抱歉！ 出现错误“*”。

## 解决方案

* 任何2.4.4、2.4.5、2.4.6或2.4.7修补程序版本上的所有商户都应将这些相应的修补程序应用于其版本。

## Patch

根据Adobe Commerce版本，使用以下附加的修补程序：

对于版本2.4.4：**[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)**

对于版本2.4.5：**[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)**

对于版本2.4.6：**[ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.4_2.4.5_2.4.6_composer.patch.zip)**

对于版本2.4.7：**[ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip](assets/ACSD-60245_Google_maps_API_2.4.7_composer.patch.zip)**

**请注意**

此问题将在8月发布的仅用于安全保护的修补程序版本中永久修复：
2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10

## 相关阅读

[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)