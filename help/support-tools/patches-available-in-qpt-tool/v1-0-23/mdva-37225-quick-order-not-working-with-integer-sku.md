---
title: 'MDVA-37225：快速订单无法使用整数SKU'
description: 适用于Adobe Commerce的MDVA-37225质量修补程序修复了在导入的SKU中存在整数值的情况下创建快速订单时页面无法加载的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23后，即可使用此修补程序。 修补程序ID为MDVA-37225。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: ecd2b9d7-ca68-4372-b0c5-55e2a3301586
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-37225：快速订单无法使用整数SKU

适用于Adobe Commerce的MDVA-37225质量修补程序修复了在导入的SKU中存在整数值的情况下创建快速订单时页面无法加载的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23时，此修补程序可用。 修补程序ID为MDVA-37225。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.4.1-p1设计的
* 该补丁还兼容本地Adobe Commerce和云基础架构2.4.1-2.4.2-p1上的Adobe Commerce

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>预修课程</u>：

已安装B2B模块的Adobe Commerce

<u>重现步骤</u>：

1. 启用B2B快速订购功能。
1. 创建4个带SKU的简单产品(示例SKU： *00100*、*001E002*、*001E02C*&#x200B;和&#x200B;*7100824*)。
1. 转到前端的``<storefront_url>/quickorder``页面，然后尝试使用具有此示例内容的CSV文件创建订单：

| sku | 数量 |
|---|---|
| 00100 | 1 |


<u>预期的结果</u>：

产品(示例： SKU = *00100*&#x200B;的产品)已按预期添加到购物车。

<u>实际结果</u>：

页面未加载，并且没有产品添加到购物车。


## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品，在我们的开发人员文档中使用以下链接：

* Adobe Commerce和Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相关阅读

要在我们的支持知识库中了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

有关QPT工具中可用的其他修补程序的信息，请参阅我们的支持知识库中的[QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)部分。
