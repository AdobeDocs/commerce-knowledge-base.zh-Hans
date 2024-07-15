---
title: “MDVA-39482：如果导入的数量为“0”且启用了延交订单，则产品缺货”
description: MDVA-39482修复了在启用MSI和延交订单并且“缺货阈值”设置为负值的情况下，如果以“0”数量导入产品，则产品缺货的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-39482。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482：如果导入的数量为“0”且启用了延交订单，则产品缺货

MDVA-39482修复了在启用MSI和延交订单并且“缺货阈值”设置为负值的情况下，如果以“0”数量导入产品，则产品缺货的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-39482。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在启用MSI和延交订单并且“缺货阈值”设置为负值时，如果以“0”数量导入，则产品缺货。

<u>先决条件</u>：

1. 必须安装MSI和示例数据。
1. 转到&#x200B;**商店** > **配置** > **目录** > **库存**：
   * 将延交订单设置为“允许数量低于0”
   * 将缺货阈值设置为“–10”

<u>重现步骤</u>：

1. 确保SKU为&#x200B;**库存**，且数量为&#x200B;**24-MB01**。
1. 导入Stock Sources的CSV。 确保在实体类型中选择“库存来源”：

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. 在导入Stock Sources后检查产品的库存状态。

<u>预期的结果</u>：

24-MB01在店面有&#x200B;**库存**。

<u>实际结果</u>：

24-MB01在店面有&#x200B;**缺货**。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
