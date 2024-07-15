---
title: '''MDVA-37224：无法通过PayFlow Pro支付“可协商报价”'
description: MDVA-37224修补程序修复了客户无法使用Paypal PayFlow Pro支付**可转让报价**的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23后，即可使用此修补程序。 修补程序ID为MDVA-37224。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: df75b38d-64c8-46b5-85ff-7606ce1dfd34
feature: B2B, Orders, Payments, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-37224：无法通过PayFlow Pro支付“可协商报价”

MDVA-37224修补程序修复了客户无法使用Paypal PayFlow Pro支付&#x200B;**可转让报价**&#x200B;的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23时，此修补程序可用。 修补程序ID为MDVA-37224。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.3.6-p1设计的
* 该补丁还兼容本地Adobe Commerce和云基础架构2.3.3-2.4.2-p1上的Adobe Commerce

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

* 已安装B2B模块的Adobe Commerce
* 已启用公司功能
* **可转让报价**&#x200B;功能已启用
* 公司用户已存在
* 已启用和配置PayPal PayFlow Pro支付方式
* PayPal PayFlow Pro付款方法允许用于B2B
* 已创建2个不同价格的产品

<u>重现步骤</u>：

1. 打开店面。
1. 将&#x200B;**产品1**&#x200B;添加到购物车。
1. 为&#x200B;**产品1**&#x200B;创建&#x200B;**可转让报价**。
1. 将&#x200B;**产品2**&#x200B;添加到购物车。
1. 从管理员处接受&#x200B;**可转让报价**（在步骤3中创建）。
1. 从店面，打开此&#x200B;**可转让报价**&#x200B;并继续结帐。
1. 在&#x200B;**审核和付款**&#x200B;步骤中选择&#x200B;**付款方式** = *PayPal PayFlow Pro*。
1. 下订单。

<u>预期的结果</u>：

* 订单按预期成功下达。
* PayPal会按预期向客户发送包含正确信息的电子邮件。

<u>实际结果</u>：

* 网页挂起，无法完成订单。
* PayPal使用零值向客户发送确认，类似于以下示例：

```php
Order ID: A1xxxxxxxxx
Order Placed: Monday, April 21, 2021 01:12:12 PM PDT

Shipping Amount: $0.00
Tax Amount: $0.00
Amount of Transaction: $0.00
Payment Type: Visa

BILL TO
--------
US
```


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 
   * [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
