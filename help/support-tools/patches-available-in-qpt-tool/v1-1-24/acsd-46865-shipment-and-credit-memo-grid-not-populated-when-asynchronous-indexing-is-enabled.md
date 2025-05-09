---
title: 'ACSD-46865：启用[!UICONTROL asynchronous indexing]时未填充[!UICONTROL shipment]和[!UICONTROL credit memo]'
description: 应用ACSD-46865修补程序以修复启用[!UICONTROL asynchronous indexing]后未填充[!UICONTROL shipment]和[!UICONTROL credit memo]网格的Adobe Commerce问题。
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865：启用[!UICONTROL asynchronous indexing]时未填充[!UICONTROL shipment]和[!UICONTROL credit memo]

ACSD-46865修补程序修复了在启用[!UICONTROL asynchronous indexing]时未填充[!UICONTROL shipment]和[!UICONTROL credit memo]网格的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-46865。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用[!UICONTROL asynchronous indexing]时未填充[!UICONTROL Shipment]和[!UICONTROL credit memo]网格。

<u>重现步骤</u>：

1. 在[!DNL Commerce]管理员中，转到&#x200B;**[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *是*。
2. 再次转到&#x200B;**[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*。
3. 清理配置缓存。
4. 为简单产品下新的访客订单。
5. 运行cron。
6. 在[!UICONTROL Commerce]管理员中打开订单，方法是转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;并生成发票和贷项通知单。
7. 将订单移动到[!UICONTROL Archive]。
8. 为简单产品创建另一个订单。
9. 运行cron。
10. 转至新订单并生成新发运、发票和贷项通知单。
11. 运行cron。
12. 检查管理员中的[!UICONTROL shipments]、[!UICONTROL invoices]和[!UICONTROL credit memo]网格。

<u>预期的结果</u>：

显示新[!UICONTROL shipment]、[!UICONTROL invoice]和[!UICONTROL credit memo]。

<u>实际结果</u>：

未显示新[!UICONTROL shipment]、[!UICONTROL invoice]和[!UICONTROL credit memo]。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
