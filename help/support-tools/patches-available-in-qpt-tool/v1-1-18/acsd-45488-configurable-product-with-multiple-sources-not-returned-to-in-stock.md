---
title: 'ACSD-45488：具有多个来源的可配置产品不会自动退货'
description: ACSD-45488修补程序解决了具有多个来源的可配置产品无法自动退订的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45488。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 83332226-b14e-4d36-bf65-170f55fff270
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-45488：具有多个来源的可配置产品不会自动退货

ACSD-45488修补程序解决了具有多个来源的可配置产品无法自动退订的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18时，此修补程序可用。 修补程序ID为ACSD-45488。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有多个来源的可配置产品不会自动返回到库存中。

<u>重现步骤</u>：

1. 创建辅助库存来源。
1. 创建具有两个关联虚拟产品的可配置产品。
1. 将关联产品分配给默认库存来源，并将数量设置为1。
1. 检查`cataloginventory_stock_status`中的`stock_status`。
1. 将两个关联产品都设置为&#x200B;*缺货*。
1. 检查`cataloginventory_stock_status`中的`stock_status`。
1. 将两个关联产品设置为&#x200B;*库存*。
1. 检查`cataloginventory_stock_status`中的`stock_status`。

<u>预期的结果</u>：

当关联产品设置为有库存时，可配置产品的库存状态将更新为&#x200B;*库存*。

<u>实际结果</u>：

当关联产品设置为有库存时，可配置产品的库存状态未更新为&#x200B;*库存*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
