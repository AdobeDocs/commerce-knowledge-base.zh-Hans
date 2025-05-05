---
title: 'MDVA-41236：无法为产品创建新计划更新或编辑现有计划更新'
description: MDVA-41236修补程序修复了以下问题：如果之前删除了“结束日期”，则用户无法为产品创建新的计划更新或编辑现有的计划更新。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41236。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 00d6c0af-f248-49f6-aaa2-3ae3c0294832
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-41236：无法为产品创建新的或编辑现有的计划更新

MDVA-41236修补程序修复了以下问题：如果之前删除了“结束日期”，则用户无法为产品创建新的计划更新或编辑现有的计划更新。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41236。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果用户之前删除了“结束日期”，则无法创建新计划或编辑产品的现有计划。

<u>重现步骤</u>：

1. 创建状态设置为&#x200B;*disable*&#x200B;的产品。
1. 添加计划更新以启用此产品。
   * 添加未来的开始和结束日期。
1. 通过删除&#x200B;**结束日期**&#x200B;来编辑计划更新。
1. 再次编辑计划并尝试添加&#x200B;**结束日期**。 将发生错误。
1. 刷新页面，然后再次转到&#x200B;**编辑计划更新**。
1. 单击&#x200B;**从更新中删除** > **删除更新**。
1. 现在，您不应在产品编辑页面顶部看到计划更新。
1. 尝试创建与上一个持续时间重叠的新计划更新。

<u>预期的结果</u>：

* 步骤4中没有错误。 由于计划尚未激活，管理员能够更新计划更新而不会出现任何错误。
* 管理员用户能够删除以前的更新并创建新更新。

<u>实际结果</u>：

用户将收到以下错误消息：

*错误：此时间范围内已存在将来更新。 请设置其他范围，然后重试。*


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修补程序部分。
