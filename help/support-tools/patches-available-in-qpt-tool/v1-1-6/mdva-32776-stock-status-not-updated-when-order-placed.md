---
title: 'MDVA-32776：库存状态未随订单投放更新'
description: MDVA-32776修补程序修复了在下订单但未发送时，库存状态未更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-32776。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776：库存状态未随订单投放更新

MDVA-32776修补程序修复了在下订单但未发送时，库存状态未更新的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-32776。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.0

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订购但未发运时，库存状态不会更新。

<u>先决条件</u>：

1. 清单模块已安装。
1. 显示缺货产品设置为&#x200B;*是*。

   若要进行设置，请转到&#x200B;**商店** > **配置** > **目录** > **库存** > **显示缺货产品** = *是*。

<u>重现步骤</u>：

1. 创建两个数量分别为11和22的简单产品。
1. 使用在第一步中创建的简单产品创建分组产品。
1. 通过将其中一个产品数量设置为11并使另一个简单产品缺货，将已分组的产品添加到购物车。
1. 完成结账并下订单。

<u>预期的结果</u>：

当关联的简单产品缺货时，分组的产品会显示`out-of-stock`标签。

<u>实际结果</u>：

1. 数量= 11的简单产品缺货。
1. 对于数量为11的产品，分组产品不显示&#x200B;*缺货*&#x200B;消息。 但是，将此产品添加到购物车会出现&#x200B;*缺货*&#x200B;错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修补程序部分。
