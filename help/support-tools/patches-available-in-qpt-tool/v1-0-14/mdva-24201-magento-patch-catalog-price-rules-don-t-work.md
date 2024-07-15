---
title: “MDVA-24201：目录价格规则不起作用”
description: MDVA-24201修补程序解决了数据库中的活动目录价格规则不适用于前端的问题。
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201：目录价格规则不起作用

MDVA-24201修补程序解决了数据库中的活动目录价格规则不适用于前端的问题。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14时，此修补程序可用。 请注意，Adobe Commerce版本2.3.5中已修复此问题。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.3上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.0 - 2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>预修课程</u>：

安装包含示例数据的新Magento实例。

<u>重现步骤</u>：

1. 登录到&#x200B;**管理员面板** > **营销** > **目录价格规则** > **添加新规则**，进行以下设置：
   1. 设置&#x200B;**规则名称**。
   1. 设置&#x200B;**活动** = *编号*
   1. 设置条件： **类别** = *4*。 （例如：包）
   1. 设置操作：
      1. 将&#x200B;**应用为**   **原始百分比**。
      1. 设置&#x200B;**折扣金额** = *10*。
      1. 保存，然后继续编辑。
   1. 单击&#x200B;**计划新更新**：
      * 设置&#x200B;**规则名称**。
      * 设置&#x200B;**活动** = *是*。
      * 保存。
1. 转到后端并运行：

   `php    bin/magento cron:run`

<u>预期的结果</u>：

按照目录价格的规定，第四类袋装产品的价格按原价的百分之十降价。

<u>实际结果</u>：

即使目录价格规则处于活动状态，也不会发生价格更改。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
