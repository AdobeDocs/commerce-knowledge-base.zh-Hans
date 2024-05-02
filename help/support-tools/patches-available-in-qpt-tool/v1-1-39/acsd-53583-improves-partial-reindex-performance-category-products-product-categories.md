---
title: '''ACSD-53583：提高的部分重新索引性能 [!UICONTROL Category Products] 和 [!UICONTROL Product Categories] 索引器'
description: 应用ACSD-53585补丁程序，以提高“类别产品”和“产品类别”索引器的部分重新索引性能。
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583：提高类别产品和产品类别索引器的部分重新索引性能

ACSD-53583修补程序改进了的部分重新索引性能， *类别产品* 和 *产品类别* 索引器。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.39。 修补程序ID为ACSD-53583。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3
* 与不兼容 [!DNL Live Search] 模块。 要将此修补程序应用到 [!DNL Live Search] 安装，请请求额外的ACSD-55719修补程序。

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

部分重新索引比完全重新索引花费的时间长。

<u>重现问题的步骤</u>：

1. 将所有索引器转换为 *按计划更新*.
1. 使用生成数据 [!DNL Performance Toolkit] （中型用户档案）。
1. 对所有产品和类别进行更改，以使它们位于索引积压中，并且所有索引都处于空闲状态。
1. 执行部分重新索引 *类别产品* 和 *产品类别* 索引器。

<u>预期结果</u>：

由于所有产品和类别都已更改，因此每个产品会调用一次部分重新索引，所用时间与完全重新索引几乎相同。

<u>实际结果</u>：

每个产品会多次调用部分重新索引，其所用时间比完全重新索引要长。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
