---
title: 'MDVA-41046：无法分配具有自定义选项的简单产品'
description: MDVA-41046修补程序解决了具有自定义选项的简单产品无法分配给可配置/分组产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41046。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046：具有自定义选项的简单产品不可用于分配

MDVA-41046修补程序解决了具有自定义选项的简单产品无法分配给可配置/分组产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41046。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有自定义选项的简单产品无法分配给可配置/分组的产品。

<u>重现步骤</u>：

1. 创建一个带有可自定义选项的简单产品，并为可配置属性设置一个值。
   * 使用&#x200B;*Color*&#x200B;作为可配置属性，并选择&#x200B;*Yellow*&#x200B;作为颜色值。
1. 保存简单产品。
1. 现在，转到创建可配置产品页面。
1. 执行“创建配置”向导，并确保选择&#x200B;*黄色*&#x200B;作为属性颜色。
1. 不保存可配置产品，从选择下拉列表中选择“选择其他产品”选项。
1. 这将打开按颜色属性黄色过滤的产品网格。 现在，选择之前使用可自定义选项创建的简单产品。
1. 保存可配置产品。

<u>预期的结果</u>：

带有自定义选项的简单产品可用于在步骤6中进行分配（在网格中可见）。

<u>实际结果</u>：

配置部分为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修补程序部分。
