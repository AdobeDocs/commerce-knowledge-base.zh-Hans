---
title: 'ACSD-46520：使用商店积分退款时订单状态不正确'
description: 本文为使用商店积分退款时用户收到错误订单状态的问题提供了解决方案。
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520：使用商店积分退款时订单状态不正确

ACSD-46520修补程序解决了使用商店积分退款时，用户得到的订单状态不正确的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-46520。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3和2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用商店积分退款时，用户会获得不正确的订单状态。

<u>重现步骤</u>：

1. 在店面创建客户帐户并登录。
1. 从管理员处将商店积分分配给客户。 店铺积分应覆盖整个订单。
1. 使用商店积分下订单。
1. 为订单开票。
1. 创建贷项通知单以退款订单的全部金额。
选中&#x200B;**[!UICONTROL Refund to store credit]**&#x200B;复选框。
1. 检查订单状态。

<u>预期的结果</u>：

订单状态为&#x200B;*已关闭*。

<u>实际结果</u>：

订单状态为&#x200B;*完成*，这不是正确的状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Quality Patches Tool指南中的[!DNL Magento Open Source]内部部署： [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=zh-Hans)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅Quality Patches Tool指南中的[[!DNL Quality Patches Tool]： Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
