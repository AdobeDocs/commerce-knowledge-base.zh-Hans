---
title: 'MDVA-37874：固定折扣不适用于整个购物车'
description: MDVA-37874修补程序修复了将整个购物车的**固定折扣金额**错误地应用于包含多个选项的捆绑产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24后，即可使用此修补程序。 修补程序ID为MDVA-37874。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874：未应用于整个购物车的固定折扣

MDVA-37874修补程序修复了将整个购物车的&#x200B;**固定折扣金额**&#x200B;错误地应用于包含多个选项的捆绑产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24时，此修补程序可用。 修补程序ID为MDVA-37874。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.4.2设计的
* 该修补程序还兼容本地Adobe Commerce以及云基础架构2.3.6-2.3.7和2.4.1-2.4.2-p1上的Adobe Commerce

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题


<u>重现步骤</u>：

1. 为整个购物车创建固定折扣金额为&#x200B;**的购物车规则**。
1. 将捆绑产品添加到购物车（捆绑产品应包含多个选定选项。）
1. 转到购物车页面，然后查看折扣。


<u>预期的结果</u>：

固定折扣金额按预期应用于整个购物车。

<u>实际结果</u>：

固定折扣金额仅应用于购物车的一部分。


## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
