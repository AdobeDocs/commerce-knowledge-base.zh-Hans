---
title: 'MDVA-39229：更新目录规则暂存更新开始时间时出错'
description: MDVA-39229修补程序修复了用户在更新目录规则暂存更新的开始时间后收到错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-39229。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: b9a203af-693d-4253-877b-591ae5f388d3
feature: Catalog Management, Staging
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-39229：更新目录规则暂存更新开始时间时出错

MDVA-39229修补程序修复了用户在更新目录规则暂存更新的开始时间后收到错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-39229。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.3.4-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户更新目录规则暂存更新的开始时间后收到错误。

<u>重现步骤</u>：

1. 创建目录价格规则。
1. 创建并执行任何暂存更新。
1. 运行查询并验证是否已创建暂存标志。


   `select * from flag;`


1. 创建新的暂存更新，以在5分钟后开始。
1. 打开&#x200B;**内容** > **暂存** > **仪表板** > **新更新**，并将开始时间延迟一分钟。
1. 等六分钟。
1. 运行cron。

<u>预期的结果</u>：

更新开始时间已更改，并且应用了更新。 从`staging_update`表中删除旧更新。

<u>实际结果</u>：

用户收到以下错误：

*report.ERROR： Cron作业staging_synchronize_entities_period出错：无法删除活动更新。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
