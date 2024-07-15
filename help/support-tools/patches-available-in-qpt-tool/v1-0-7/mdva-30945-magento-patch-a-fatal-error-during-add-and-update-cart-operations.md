---
title: 'MDVA-30945：添加和更新购物车操作期间发生致命错误'
description: MDVA-30945修补程序修复了在更新购物车时，在module-configurable-product CartItemProcessor.php*中的null上收到致命错误*调用成员函数getValue()的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 已在Adobe Commerce 2.4.2中修复此问题。
exl-id: 0950e91b-900b-421d-91e7-abbfca4f30be
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# MDVA-30945：添加和更新购物车操作期间发生严重错误

MDVA-30945修补程序修复了在更新购物车时在module-configurable-product CartItemProcessor.php *中的null上收到致命错误*&#x200B;调用成员函数getValue()的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在管理员中更新购物车中的产品后出现致命的PHP错误。

<u>重现步骤</u>：

1. 在Commerce管理员中，创建不带选项的可配置产品。
1. 将其添加到店面的购物车中。
1. 返回到管理员，向产品添加可配置选项并保存更改。
1. 刷新店面上的购物车页面。

<u>预期的结果</u>：

在购物车页面上，显示以下验证消息： *以下某些产品没有所有必需选项*。

<u>实际结果</u>：

购物车页面为空白。 在PHP `error.log`中，记录了以下错误： vendor/magento/module-configurable-product/Model/Quote/Item/CartItemProcessor.php：76 *中的*&#x200B;未捕获异常“错误”，消息为“Null上的成员函数getValue()的调用”

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
