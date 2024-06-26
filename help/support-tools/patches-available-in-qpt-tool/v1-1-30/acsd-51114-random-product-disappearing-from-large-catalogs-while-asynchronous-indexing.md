---
title: 'ACSD-51114：启用异步索引后，随机产品从大型目录中消失'
description: 应用ACSD-51114修补程序以修复Adobe Commerce问题。启用异步索引后，大型目录中随机产品消失。
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114：启用异步索引后，随机产品从大型目录中消失

>[!NOTE]
>
>此修补程序已弃用。

ACSD-51114修补程序修复了在启用异步索引后，随机产品从大型目录中消失的问题。 此修补程序在以下情况下可用： [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.30。 修补程序ID为ACSD-51114。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查[[!DNL Quality Patches Tool]：搜索修补程序页面]。使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用异步索引后，随机产品从大型目录中消失。

<u>重现问题的步骤</u>：

1. 创建一组10个产品。
1. 将所有索引器设置为 **[!UICONTROL Update on Save]** 模式。
1. 创建一个类别并将所有产品分配给该类别。
1. 禁用所有产品。
1. 打开类别并验证那里没有产品。
1. 将所有索引器设置为 **[!UICONTROL Update on Schedule]** 模式。
1. 设置 `DEFAULT_BATCH_SIZE` 到2英寸  `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. 按照以下顺序启用产品：1、9、2、5、10、3。
1. 运行cron命令。
1. 再次打开类别。

<u>预期结果</u>：

将显示所有启用的产品。

<u>实际结果</u>：

未显示所有启用的产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
