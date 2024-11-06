---
title: 'MDVA-31763：将还原目录价格规则，直到手动重新索引为止'
description: MDVA-31763修补程序解决了在手动重新索引之前恢复目录价格规则的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-31763。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: eb2dfd1a-6d12-4676-82c1-bf92c6fa9fda
feature: Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-31763：将还原目录价格规则，直到手动重新编入索引

MDVA-31763修补程序解决了在手动重新索引之前恢复目录价格规则的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-31763。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对可配置产品执行`catalogrule_product`部分索引器时，目录规则消失。

<u>重现步骤</u>：

1. 登录到管理员后端。
1. 转到&#x200B;**商店** > **属性** > **产品**&#x200B;并搜索“制造商”属性。
   * 添加几个选项并将“用于促销规则条件”设置为&#x200B;*是*。
1. 转到&#x200B;**存储** > **属性** > **属性集**。
   * 选择默认属性集并添加“manufacturer”属性。
1. 创建具有几个变体的可配置产品。
1. 为之前创建的可配置产品设置“制造商”属性值。
1. 创建目录规则：
   * 活动=是
   * 网站=主网站
   * 客户组=未登录
   * 条件：制造商= \&lt;可配置产品的选定值>
   * 操作：任何折扣
1. 执行完整索引。
1. 检查PDP上的产品价格，并确保价格正确。
1. 更新已创建的可配置产品的“权重”属性。
1. 检查PDP上的产品价格。

<u>预期的结果</u>：

在部分重新索引期间，不会删除针对可配置产品设置的目录价格规则。

<u>实际结果</u>：

对可配置产品设置的目录价格规则在部分重新索引期间消失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
