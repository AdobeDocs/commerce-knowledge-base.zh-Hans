---
title: 'MDVA-42410：优惠券报表仅显示默认基本货币'
description: MDVA-42410修补程序修复了优惠券报表仅显示基础货币的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42410。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: b442a2ce-1bd4-4f09-95fd-2c626e32f509
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-42410：优惠券报表仅显示默认基本货币

MDVA-42410修补程序修复了优惠券报表仅显示基础货币的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42410。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

优惠券报表仅显示默认基础货币。

<u>重现步骤</u>：

1. 创建其他网站、商店和商店视图。
1. 为此新网站设置其他货币。 例如，欧元。
1. 转到&#x200B;**商店** > **汇率**&#x200B;并将汇率配置为&#x200B;**欧元**。
1. 创建具有特定优惠券的&#x200B;**购物车价格规则** - **测试**。
1. 转到前端，在新网站上使用&#x200B;**测试**&#x200B;优惠券下订单。
1. 转到&#x200B;**报表** > **销售** > **优惠券**。
1. 在范围下拉列表中选择新网站。
1. 刷新统计信息并运行报告。

<u>预期的结果</u>：

优惠券报表会将新网站的货币显示为欧元。

<u>实际结果</u>：

新网站的优惠券报表中使用默认基本货币（本例中为USD）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
