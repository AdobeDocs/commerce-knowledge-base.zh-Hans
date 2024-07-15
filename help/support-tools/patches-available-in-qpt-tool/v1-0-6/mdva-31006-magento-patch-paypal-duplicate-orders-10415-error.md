---
title: 'MDVA-31006：Paypal重复订单10415错误'
description: MDVA-31006修补程序修复了以下问题：使用PayPal Express结帐付款创建重复订单时出现10415错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 已在Adobe Commerce 2.4.2中修复此问题。
exl-id: ff471fd3-f580-4149-83bc-67f6fce8e28d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# MDVA-31006：Paypal重复订单10415错误

MDVA-31006修补程序修复了以下问题：使用PayPal Express结帐付款创建重复订单时出现10415错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6时，此修补程序可用。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.3.2 - 2.4.0

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

系统没有将用户发送到Adobe Commerce订单成功页面，因此他们刷新了空白页面，然后下了第二个订单，从而导致订单重复。

<u>先决条件</u>：

* 已安装Adobe Commerce。
* 已配置PayPal Express签出付款。
* 登录到Commerce管理员。 转到&#x200B;**商店** > **配置** > **销售** > **付款方式** >选择&#x200B;**Paypal Express结帐** > **配置** > **高级设置** > **跳过订单审核步骤** > *否*。

<u>重现步骤</u>：

1. 以用户身份登录。
1. 选择项目并单击&#x200B;**添加到购物车**。
1. 单击购物车，然后单击&#x200B;**继续结帐**。
1. 进入PayPal Express窗口进行付款。
1. 您将被重定向至“Adobe Commerce订单审核”页面。
1. 按&#x200B;**下订单**&#x200B;按钮。
1. 由于服务器基础架构问题而模拟系统错误。 用户将看到一个空白页。
1. 刷新页面。

<u>预期的结果</u>：

* 客户将被重定向到“订单复查”页面，并看到错误消息“*成功的付款交易已完成。 请检查订单是否已下达。*”
* 在`/var/log/payment.log`中的payment.log中，10415有错误，但只创建了一个订单。

<u>实际结果</u>：

* 由于客户未发送到Adobe Commerce订单成功页面，因此他们刷新了空白页面，然后又下了第二张订单，从而创建了两个重复的订单。
* 在`/var/log/payment.log`中的payment.log中，10415有错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
