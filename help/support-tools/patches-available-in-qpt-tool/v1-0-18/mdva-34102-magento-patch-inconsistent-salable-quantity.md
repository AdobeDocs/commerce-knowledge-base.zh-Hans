---
title: 'MDVA-34102：可销售数量不一致'
description: MDVA-34102修补程序解决了产品网格和“管理”中的“编辑产品”页面上禁用产品的默认库存量为零的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18后，即可使用此修补程序。 修补程序ID为MDVA-34102。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: cb1d4689-c122-4afd-8597-b2627027aaf3
feature: Variables
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-34102：可销售数量不一致

MDVA-34102修补程序解决了产品网格和“管理”中的“编辑产品”页面上禁用产品的默认库存量为零的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18时，此修补程序可用。 修补程序ID为MDVA-34102。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 设置两个包含商店和商店视图的网站。
1. 创建附加源和库存。
1. 添加简单的产品：
   * 设置&#x200B;**启用产品** = *否*。
   * 分配两个数量大于零且具有&#x200B;**Source物料状态** = *库存*&#x200B;的来源（示例： **默认库存** = *123*&#x200B;和&#x200B;**英国库存** = *123*）。
1. 保存产品。
1. 检查&#x200B;**产品可销售数量**&#x200B;选项卡。

<u>预期的结果</u>：

默认股票和英国股票= *123.*

在“产品网格”和“管理”的“编辑产品”页面上，已禁用的产品的默认库存数量可正确显示。

<u>实际结果</u>：

默认库存= *0*，英国库存= *123.*

在“产品网格”和“管理”的“编辑产品”页面上，已禁用产品的默认库存数量为零。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
