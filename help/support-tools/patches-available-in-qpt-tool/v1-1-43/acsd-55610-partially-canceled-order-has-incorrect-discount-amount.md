---
title: 'ACSD-55610：部分取消的订单的折扣金额不正确'
description: 应用ACSD-55610补丁以修复部分取消的订单折扣金额不正确的Adobe Commerce问题。
feature: Invoices, Orders, Price Rules, Shopping Cart
role: Admin, Developer
exl-id: f4cca4fa-dc04-4c86-9176-c648b1d0e732
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-55610：部分取消的订单的折扣金额不正确

ACSD-55610修补程序修复了部分取消的订单的折扣金额不正确的问题。 此修补程序在以下情况下可用： [!DNL Quality Patches Tool (QPT)] 已安装1.1.43。 修补程序ID为ACSD-55610。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新版本的其他版本 [!DNL Quality Patches Tool] 版本发布。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

部分取消的订单的折扣金额不正确。

<u>重现问题的步骤</u>：

1. 创建购物车价格规则。

   * *[!UICONTROL Rule Name]*： *冬季促销*
   * *[!UICONTROL Active]* = *是*
   * *[!UICONTROL Websites]* = *主网站*
   * 选择所有客户组。
   * 选择特定优惠券。
   * *[!UICONTROL Coupon Code]*： *WINTER10*
   * *[!UICONTROL Conditions]*： *[!UICONTROL If ALL of these conditions are TRUE]*： *小计(不包括 税额)等于或大于75*
   * 应用 *[!UICONTROL Percent of product price discount]*.
   * *[!UICONTROL Discount Amount]*： *10*
   * *[!UICONTROL Discard subsequent rules]*： *是*

1. 创建三个价格设置为100的产品。
1. 将三个产品添加到购物车。
1. 申请优惠券。
1. 下订单。
1. 为订单中的一个项目开票并装运它。
1. 取消其他两个项目。
1. 查看 `base_discount_canceled` 列。

<u>预期结果</u>：

中的折扣金额 `base_discount_cancelled` 正确反映。

<u>实际结果</u>：

此 `base_discount_cancelled` 是不对的。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在 [!DNL Quality Patches Tool] 指南。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) 云基础架构上的Commerce指南中的。

## 相关阅读

要了解有关 [!DNL Quality Patches Tool]，请参阅：

* [[!DNL Quality Patches Tool] 已发布：用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用以下方式检查修补程序是否可用于您的Adobe Commerce问题 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在 [!DNL Quality Patches Tool] 指南。
