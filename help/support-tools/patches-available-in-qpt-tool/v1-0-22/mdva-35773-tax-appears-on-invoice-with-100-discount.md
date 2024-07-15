---
title: 'MDVA-35773：发票上显示的税有100%折扣'
description: MDVA-35773修补程序修复了发票上折扣为100%的订单的Grand Total未显示为零的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22后，即可使用此修补程序。 修补程序ID为MDVA-35773。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 895cb7d3-be9f-4864-9658-87ee0471f556
feature: Invoices, Marketing Tools, Orders, Personalization, Taxes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-35773：税显示在发票上，折扣为100%

MDVA-35773修补程序修复了发票上折扣为100%的订单的Grand Total未显示为零的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.22时，此修补程序可用。 修补程序ID为MDVA-35773。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.6-2.3.7和2.4.1-2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 导航到&#x200B;**商店** > **设置** > **配置** > **销售** > **税费**。
1. 设置&#x200B;**目录价格**&#x200B;和&#x200B;**应用价格折扣**&#x200B;至&#x200B;*含税*。
1. 导航到&#x200B;**商店** > **税则** > **添加新税则**。
1. 创建税则（例如：税率为10%的所有美国）并应用它。
1. 导航到&#x200B;**营销** > **购物车价格规则**，然后&#x200B;**添加新规则**。
1. 为所有用户创建&#x200B;**100%折扣的规则**。
1. 在店面下订单：

   * 选择&#x200B;**免运费**。
   * 应用&#x200B;**优惠券代码**。

1. 导航到&#x200B;**Sales** > **Orders**，然后打开您的订单。
1. 为订单创建发票，然后将其打开。

<u>预期的结果</u>：

发票总计= *$0.00*。

<u>实际结果</u>：

已创建发票总计= *税额*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
