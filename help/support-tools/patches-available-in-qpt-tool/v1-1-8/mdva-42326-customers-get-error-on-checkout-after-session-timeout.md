---
title: 'MDVA-42326：会话超时后客户在签出时出错'
description: MDVA-42326修补程序解决了即使在启用了永久购物车的情况下，客户在会话超时后结账时出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-42326。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326：会话超时后客户在签出时出错

MDVA-42326修补程序解决了即使在启用了永久购物车的情况下，客户在会话超时后结账时出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8时，此修补程序可用。 修补程序ID为MDVA-42326。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使启用了永久购物车，客户在会话超时后也会在结账时遇到错误。

<u>先决条件</u>：

1. 转到&#x200B;**配置** > **常规** > **Web** > **默认Cookie设置** > **Cookie生命周期**，并设置为&#x200B;**120**。
1. 转到&#x200B;**配置** > **客户** > **客户配置** > **在线客户选项**，并将这两个值都设置为&#x200B;**2**。
1. 转到&#x200B;**配置** > **客户** > **永久购物车**，并设置为&#x200B;**启用**。
1. 转到&#x200B;**配置** > **销售** > **付款方式**&#x200B;并关闭除&#x200B;**支票/汇票**&#x200B;之外的所有付款方式（应启用它）。

<u>重现步骤</u>：

1. 以客户身份登录并将一些产品添加到购物车。
1. 检查购物车。
1. 等待两分钟（在前提条件中设置）；会话应超时。
1. 单击&#x200B;**转到签出**，并且不刷新页面。
1. 结帐为来宾，填写送货地址并选择送货方式。
1. 单击&#x200B;**下一步**。
1. 在&#x200B;**复查和付款**&#x200B;页面上，单击&#x200B;**下订单**。 由于只允许一种付款方式，因此客户无需选择付款方式即可下订单。

<u>预期的结果</u>：

客户应该能够下订单。

<u>实际结果</u>：

客户收到以下错误： *地址验证失败：电子邮件的格式错误*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
