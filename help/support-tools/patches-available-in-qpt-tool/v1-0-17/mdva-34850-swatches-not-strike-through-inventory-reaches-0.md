---
title: '''MDVA-34850：样本未删除清单达到“0”'
description: MDVA-34850修补程序修复了以下问题：当库存达到“0”时，样本不会被清除，并且不会出现在链接到任何其他现有样本的产品详细信息页面(PDP)链接中。 在管理员配置中，**显示缺货产品**也设置为*是*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: 90f5cef4-137a-426d-a447-2d1aca23e6c1
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# MDVA-34850：样本未删除清单达到“0”

MDVA-34850修补程序修复了以下问题：当库存达到“0”时，样本不会被清除，并且不会出现在链接到任何其他现有样本的产品详细信息页面(PDP)链接中。 在管理员配置中，**显示缺货产品**&#x200B;也设置为&#x200B;*是*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17时，此修补程序可用。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.1 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当默认库存库存未使用且启用了&#x200B;**显示缺货产品**&#x200B;配置时，缺货产品选项不会显示在PDP页面上。

<u>先决条件</u>：

* 安装多Source清单(MSI)。
* 在[库存库存库存选项](https://docs.magento.com/user-guide/configuration/catalog/inventory.html)中启用显示缺货产品。

<u>重现步骤</u>：

1. 创建新库存库存\[新库存\]，将所有网站分配给该库存和上述来源。 现在，不应使用“默认库存”。
1. 添加三个大小选项\[S，M，L\]，创建一个[可配置产品](https://docs.magento.com/user-guide/catalog/product-create-configurable.html)。
1. 打开每个选项，并通过仅指定创建的自定义源\[new\_source\]来添加数量。 此外，将\[Source Status\]设置为\[In Stock\]。
1. 从前端重新索引并检查可配置产品。 所有三个选项都应可见。
1. 从后端打开分配给\[size：S\]的简单产品并将\[Source Status\]设置为\[缺货\]，同时将数量更新为0。 从前端重新索引并检查可配置产品。

<u>预期的结果</u>：

由于启用了“显示缺货产品”选项，因此应显示所有三个选项。 应禁用缺货选项\[S\]并将其清除。 它应显示2个（共1个）选件产品，价格= 12x2，以便在前端和后端显示订单详细信息。

<u>实际结果</u>：

缺货选项处于隐藏状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
