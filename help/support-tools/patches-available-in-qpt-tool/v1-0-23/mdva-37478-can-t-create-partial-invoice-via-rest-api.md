---
title: “MDVA-37478：无法通过REST API创建部分发票”
description: MDVA-37478修补程序修复了以下问题：对于使用付款方式**帐户付款**下达的订单，您无法通过REST API创建部分发票。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23后，即可使用此修补程序。 修补程序ID为MDVA-37478。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。
exl-id: 1b235baa-a188-467c-8ae5-de0836bc2caa
feature: REST, B2B, Invoices
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-37478：无法通过REST API创建部分发票

MDVA-37478修补程序修复了无法通过REST API为使用付款方式&#x200B;**帐户付款**&#x200B;下达的订单创建部分发票的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.23时，此修补程序可用。 修补程序ID为MDVA-37478。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

* 该补丁是为Adobe Commerce on cloud infrastructure 2.3.3-p1设计的
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.0-2.3.7上的Adobe Commerce

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>预修课程</u>：

已安装B2B模块的Adobe Commerce

<u>重现步骤</u>：

1. 启用&#x200B;**B2B公司**。
1. 启用&#x200B;**帐户付款**&#x200B;付款方式。
1. 创建2个简单的产品。
1. 创建公司帐户。
1. 添加超过2个已创建产品的总价的公司积分。
1. 使用创建的公司帐户登录到前端。
1. 将创建的2个产品添加到购物车，然后使用&#x200B;**帐户付款**&#x200B;付款方式结帐。
1. 尝试为通过REST API创建的订单创建部分发票：

   ```php
   POST /rest/V1/order//invoice
   {
     "items": [
       {
         "order_item_id": 2,
         "qty": 1
       }
     ]
   }
   ```

<u>预期的结果</u>：

按预期为使用&#x200B;**帐户付款**&#x200B;付款方式发出的订单创建了部分发票。

<u>实际结果</u>：

从REST API返回以下错误：

```php
{"message":"Invoice Document Validation Error(s):\nAn invoice for partial quantities cannot be issued for this order. To continue, change the specified quantity to the full quantity."}
```

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
