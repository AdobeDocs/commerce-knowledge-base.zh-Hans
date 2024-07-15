---
title: 'MDVA-31150：没有商店信用信息的发票'
description: MDVA-31150修补程序修复了在没有存储信用信息的情况下创建发票的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8后，即可使用此修补程序。 请注意，此问题将在Adobe Commerce版本2.4.2中修复。
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150：没有商店信用信息的发票

MDVA-31150修补程序修复了在没有存储信用信息的情况下创建发票的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8时，此修补程序可用。 请注意，此问题将在Adobe Commerce版本2.4.2中修复。

## 受影响的产品和版本

* 此补丁是为Cloud Infrastructure 2.3.5-p2上的Adobe Commerce设计的。
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.0到2.3.5-p2以及2.4.0到2.4.0-p1上的Adobe Commerce。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在通过API发出发票订单后，发票中不存在已使用的客户余额和礼品卡信息。

<u>重现步骤</u>

1. 向客户帐户添加商店信用额度：在管理员侧边栏上，转到&#x200B;**客户** > **所有客户。**
1. 查找客户记录并单击“操作”列中的&#x200B;**编辑**，然后单击&#x200B;**存储信用** >更新余额> **保存客户**。
1. 转到Storefront并将产品添加到购物车。
1. 以商店信用卡或礼品卡金额作为部分付款下达订单。
1. 使用有效负荷为`REST API>POST>/rest/V1/order/1/invoice`创建发票：    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. 获取刚刚使用`REST API>GET>/rest/V1/invoices/1`创建的发票。

<u>预期的结果</u>

通过API调用返回商店信用卡和礼品卡余额。

<u>实际结果</u>

API调用不会返回商店信用卡和礼品卡余额。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
