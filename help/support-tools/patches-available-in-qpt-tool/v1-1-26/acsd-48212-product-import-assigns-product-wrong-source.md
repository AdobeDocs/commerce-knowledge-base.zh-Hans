---
title: 'ACSD-48212：产品导入将产品分配给错误的源'
description: 应用ACSD-48212修补程序以修复Adobe Commerce问题，该问题导致产品导入将产品分配给错误的源。
exl-id: b3426f62-f73a-4b76-8e0e-544a9133720f
feature: Admin Workspace, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-48212：产品导入将产品分配给错误的源

ACSD-48212修补程序修复了产品导入将产品分配给错误源的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-48212。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品导入将产品分配给错误的源。

<u>重现步骤</u>：

1. 创建辅助库存来源。
1. 创建仅具有默认库存来源的产品。
1. 导出产品。
1. 运行`bin/magento cron:run`。
1. 打开&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**。
1. 从网格中选择产品。
1. 使用&#x200B;*[!UICONTROL mass action]*&#x200B;菜单取消分配库存。
1. 运行`bin/magento cron:run`。
1. 使用&#x200B;*[!UICONTROL mass action]*&#x200B;菜单分配次源。
1. 运行`bin/magento cron:run`。
1. 使用&#x200B;*[!UICONTROL mass action]*&#x200B;菜单删除产品。
1. 运行`bin/magento cron:run`。
1. 使用之前导出的CSV导入产品。
1. 检查源分配。

<u>预期的结果</u>：

产品仅分配给默认源。

<u>实际结果</u>：

产品同时分配给默认来源和辅助来源。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
