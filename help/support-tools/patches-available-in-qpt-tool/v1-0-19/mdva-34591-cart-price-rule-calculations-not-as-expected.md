---
title: 'MDVA-34591：购物车价格规则计算不符合预期'
description: MDVA-34591修补程序修复了以下问题：如果应用了多个购物车价格规则，则具有**最大数量折扣应用于**的购物车价格规则将无法正常工作。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-34591。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: 1fa196bb-aab1-4364-a1b0-7c31d6d27d6d
feature: Orders, Price Rules, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# MDVA-34591：购物车价格规则计算不符合预期

MDVA-34591修补程序修复了使用购物车价格规则的问题 **最大数量折扣应用于** 如果应用了多个购物车价格规则，则无法正常工作。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.19。 修补程序ID为MDVA-34591。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u>：

1. 转到“管理员”，创建以下两个规则：

   * 规则1：购物车中最多三件物品优惠$10。 设置优先级= *3*.
   * 规则2：购物车中所有产品优惠50%。 设置优先级= *1*.

1. 去店面。

1. 将产品集的八个数量添加至价格= *51美元* 都送到了购物车。

1. 检查购物车中的折扣金额。

<u>预期结果</u>：

正确计算的折扣为234美元，与预期一致。

* 计算：

  匹配购物车价格规则：规则2，规则1\
  应用规则2（50%优惠），因此折扣= $204\
  应用规则1（3项10折），因此折扣= $30\
  总折扣=最小值( 408/2 + 10x3， 8 &#42; 51) =最小值(204 + 30， 8 &#42; 51) = $234

<u>实际结果</u>：

由于用于计算最大折扣值的数量错误，将折扣错误地计算为$153，因为无论购物车中的产品金额如何，都应用固定的折扣金额。

* 计算：

  匹配购物车价格规则：规则2，规则1\
  应用规则2（50%优惠），因此折扣= $204\
  应用规则1（3项10折），因此折扣= $30\
  总折扣=最小值(204 + 30， 3 &#42; 51) = $153

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
