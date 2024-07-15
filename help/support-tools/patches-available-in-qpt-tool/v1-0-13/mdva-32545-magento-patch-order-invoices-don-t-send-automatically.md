---
title: “MDVA-32545修补程序：订单发票不会自动发送”
description: MDVA-32545修补程序修复了以下问题：发票电子邮件不会针对管理员下达的订单自动发送给客户。 这影响任何具有**Sale**交易类型的支付方式，如**Braintree**或**PayPal Payflow Pro**。
exl-id: 682eaeb1-5475-4d37-9536-0605f5b9f163
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# MDVA-32545修补程序：订单发票不会自动发送

MDVA-32545修补程序修复了以下问题：发票电子邮件不会针对管理员下达的订单自动发送给客户。 这会影响任何具有&#x200B;**Sale**&#x200B;交易类型的付款方式，如&#x200B;**Braintree**&#x200B;或&#x200B;**PayPal Payflow Pro**。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.2-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 使用&#x200B;**Sale**&#x200B;交易记录类型启用任何付款方式。 (例如：**Braintree**&#x200B;或&#x200B;**PayPal Payflow Pro**。)
1. 创建一个简单的产品。
1. 在前端创建客户帐户。
1. 向管理员下单。

<u>预期的结果</u>：

发票电子邮件会按预期自动发送给客户。

<u>实际结果</u>：

发票电子邮件不会自动发送给客户。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
