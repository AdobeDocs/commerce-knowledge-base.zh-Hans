---
title: 'MDVA-37082：分组产品的库存状态部分索引不正确'
description: MDVA-37082Magento修补程序修复了当自定义股票的已分组产品的股票状态部分索引错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25后，即可使用此修补程序。 修补程序ID为MDVA-37082。 请注意，此问题计划在Magento2.4.4中修复。
exl-id: 1c0abc99-bd24-4848-87a3-227a63655cb7
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-37082：已分组产品的库存状态部分索引不正确

MDVA-37082Magento修补程序修复了当自定义股票的已分组产品的股票状态部分索引错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25时，此修补程序可用。 修补程序ID为MDVA-37082。 请注意，此问题计划在Magento2.4.4中修复。


## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：**
Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.4.2-p1
>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在共享子项时，对分组产品子产品的增量索引可能会导致不正确的其他分组产品索引不正确。

<u>重现步骤</u>：

* 为主网站创建新的库存和来源。
* 创建3个数量为10、15和0的简单产品。
* 创建2个分组的产品，并将第一个简单产品与数量10的其中一个产品以及其他2个简单产品分配给另一个简单产品。
* 确认可从前端以库存方式访问两个分组产品。
* 将数量0的简单产品分配给第一个分组产品的追加销售产品。
* 清理全页缓存，并从前端检查第二组产品。
* 运行完全重新索引。
* 从前端检查第二个分组产品。
* 保存第一个分组的产品。
* 清理全页缓存，并从前端检查第二组产品。

<u>预期的结果</u>：

使用追加销售保存另一个分组产品后，分组产品没有缺货。 在完全重新索引后，该问题得以解决。

<u>实际结果</u>：

保存第一个分组产品时，第二个分组产品缺货。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce部署方法，使用以下指向我们的开发人员文档的链接：

* Adobe Commerce内部部署：开发人员文档中的[软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查Magento问题是否有可用的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
