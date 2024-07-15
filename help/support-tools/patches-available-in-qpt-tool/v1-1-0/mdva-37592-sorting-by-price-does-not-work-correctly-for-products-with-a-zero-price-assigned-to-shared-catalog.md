---
title: 'MDVA-37592：按价格排序不适用于价格为零的产品'
description: MDVA-37592 Adobe Commerce修补程序解决了按价格排序对分配给共享目录且价格为零的产品无法正常工作的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-37592。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 30ac1e87-c32d-4e79-9ed9-d1861061d760
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-37592：按价格排序不适用于价格为零的产品

MDVA-37592 Adobe Commerce修补程序解决了按价格排序对分配给共享目录且价格为零的产品无法正常工作的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0时，此修补程序可用。 修补程序ID为MDVA-37592。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署类型） 2.3.6-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于分配给共享目录且价格为零的产品，按价格排序无法正确运行。

<u>先决条件</u>：

已安装B2B。

<u>重现步骤</u>：

1. 启用共享目录。
1. 使用以下价格创建四个产品，并将它们分配给一个类别 — $50、$60、$70和$80。
1. 使用上述产品创建共享目录。
1. 将价格为$70的产品自定义价格设置为零。
1. 现在创建公司用户，并将其分配给刚刚创建的共享目录。
1. 使用公司帐户登录，并浏览到产品被分配到的类别。
1. 尝试按价格排序。

<u>预期的结果</u>：

对价格为零的产品进行了正确排序。

<u>实际结果</u>：

价格为零的产品未正确排序。 而是按照原价排序。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* 在我们的开发人员文档中，将Adobe Commerce内部部署：[软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 我们的云架构上的Adobe Commerce：开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
