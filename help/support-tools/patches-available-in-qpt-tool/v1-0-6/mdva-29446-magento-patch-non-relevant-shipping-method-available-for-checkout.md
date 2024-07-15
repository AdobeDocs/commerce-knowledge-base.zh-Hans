---
title: 'MDVA-29446：可用于签出的不相关配送方式'
description: MDVA-29446修补程序解决了以下问题：在结账送货方法选项上显示不适用的送货方法，并且如果选中此项，则会显示错误消息“*未找到具有此类方法的运营商null，统一费率*”。 显示。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 该问题计划在其后Adobe Commerce版本中修复。
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446：可用于签出的不相关配送方式

MDVA-29446修补程序解决了以下问题：在签出配送方式选项上显示不适用的配送方式，并且如果选中此配送方式，则显示错误消息“*未找到具有此类方法的空运营商，统一费率*”。 显示。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6时，此修补程序可用。 该问题计划在其后Adobe Commerce版本中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.3-2.4.0。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

您有一个不适用的配送方式，但仍显示在结帐配送方式选项中，您可以选择此不相关的配送方式。

<u>重现步骤</u>：

1. 安装clean 2.3-develop。
1. 启用统一速率并设置：

   * 发货到适用的国家/地区= *特定的国家/地区*
   * 发运到特定国家/地区= *南极洲*
   * 如果不适用，则显示方法= *是*

1. 禁用所有其他配送方式。
1. 转到前端，创建一个具有美国地址的客户。
1. 选择项目并单击&#x200B;**添加到购物车**。
1. 单击购物车，然后单击&#x200B;**继续结帐**。

<u>实际结果</u>：

1. 在&#x200B;**送货**&#x200B;页面上，您会看到以下内容：

   * 统一比率可见
   * 统一费率是$0
1. 用户单击&#x200B;**下一步**&#x200B;后，用户出现以下错误：

*“未找到具有此类方法的运营商： null， flatrate”*

<u>预期的结果</u>：

* 如果配送方式不适用，则配送方式的价格将不可见。
* **下一步**&#x200B;按钮不应处于活动状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
