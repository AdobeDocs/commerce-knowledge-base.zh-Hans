---
title: 'MDVA-33970修补程序：贷项通知单中的货币签名'
description: MDVA-33970修补程序解决了在贷项通知单中显示美元($)符号而非本地化货币的问题。 当**Website**范围用于**Price**属性时，会发生这种情况。
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# MDVA-33970修补程序：贷项通知单中的货币签名

MDVA-33970修补程序解决了在贷项通知单中显示美元($)符号而非本地化货币的问题。 当&#x200B;**网站**&#x200B;范围用于&#x200B;**价格**&#x200B;属性时，会发生这种情况。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15时，此修补程序可用。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.4-p2上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.4 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>前提条件</u>：

在本例中，使用以下设置：

* 2个网站存在 — 每个网站都有&#x200B;**商店**&#x200B;和&#x200B;**商店视图**。
* **默认配置**&#x200B;的新加坡元为&#x200B;**货币** （**商店>配置>常规>货币设置**）：
   * **基本货币** = *新加坡元*
   * **默认显示货币** = *新加坡元*
   * **允许的货币** = *新加坡元*
* **网站1**&#x200B;具有&#x200B;**默认配置**。
* **网站2**&#x200B;使用马来西亚林吉特作为&#x200B;**货币**：
   * **基本货币** = *马来西亚林吉特*
   * **默认显示货币** = *马来西亚林吉特*
   * **允许的货币** = *马来西亚林吉特*
* 转到&#x200B;**存储>货币符号**，并设置：
   * **MYR （马来西亚林吉特）** = *RM*
   * **SGD （新加坡元）** = *SGD* （**使用标准** = *已核取*）
* 某些&#x200B;**产品**&#x200B;存在。

<u>重现步骤</u>：

1. 从&#x200B;**网站2**&#x200B;发出&#x200B;**订单**（您可以将其设置为默认以避免其他设置）。
1. 登录到&#x200B;**管理员**。
1. 打开新创建的订单。
1. 检查&#x200B;**货币符号** = *RM*。
1. 创建&#x200B;**发票**。
1. 检查发票中的&#x200B;**货币符号** = *RM*。
1. 创建&#x200B;**贷项通知单**。
1. 检查&#x200B;**贷项通知单**&#x200B;中的&#x200B;**货币符号****** = *RM*。
1. 在&#x200B;**订单**&#x200B;中打开&#x200B;**贷项通知单**&#x200B;选项卡。
1. 检查网格中的&#x200B;**货币符号**。
1. 打开&#x200B;**销售>贷项通知单**。
1. 检查网格中的&#x200B;**货币符号**。

<u>预期的结果</u>：

使用正确的本地化货币符号（如预期）。

<u>实际结果</u>：

美元符号($)已使用，即使未在管理员设置中进行设置也是如此。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
