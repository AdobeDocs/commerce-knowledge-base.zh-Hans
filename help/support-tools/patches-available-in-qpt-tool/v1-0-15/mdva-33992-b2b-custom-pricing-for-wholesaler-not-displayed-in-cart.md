---
title: 'MDVA-33992：购物车中未显示批发商的B2B自定义定价'
description: MDVA-33992修补程序修复了在将产品添加到购物车时未反映B2B客户的自定义定价的问题。 安装Quality Patches Tool (QPT) 1.0.15后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 6018fae6-762c-46c6-9497-ecf090115b7f
feature: B2B, Catalog Management, Orders, Shopping Cart
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-33992：购物车中未显示批发商的B2B自定义定价

MDVA-33992修补程序修复了在将产品添加到购物车时未反映B2B客户的自定义定价的问题。 安装Quality Patches Tool (QPT) 1.0.15后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**在带有B2B的Adobe Commerce基础架构2.4.1上为Adobe Commerce版本**&#x200B;创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和带有B2B的Adobe Commerce内部部署2.3.0-2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将产品添加到购物车时，不会反映B2B客户的自定义定价。

<u>重现步骤</u>：

对于启用了共享目录的B2B版本，此问题可重现自述。

1. 创建分配了自定义共享目录的B2B公司。
1. 在公司的自定义目录中使用自定义价格（层价格）创建产品。
1. 作为B2B客户，检查目录是否显示了自定义产品价格。
1. 作为B2B客户，将产品添加到购物车。

<u>预期的结果</u>：

正确的价格将显示在购物车中，并与目录中的价格匹配。

<u>实际结果</u>：

自定义价格将消失，并显示默认目录中的常规价格。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
