---
title: 'MDVA-31640修补程序：无法通过REST API创建连续的计划更新'
description: MDVA-31640修补程序修复了以下问题：如果更新的开始日期与以前存在的更新的结束日期一致，则无法使用REST API为多个商店创建针对特殊价格的新计划更新。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 8d91db3d-7c94-4757-8087-4cf53cad81e7
feature: REST
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# MDVA-31640修补程序：无法通过REST API创建连续的计划更新

MDVA-31640修补程序修复了以下问题：如果更新的开始日期与以前存在的更新的结束日期一致，则无法使用REST API为多个商店创建针对特殊价格的新计划更新。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.5-p1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.1 - 2.3.5-p2、2.4.0、2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了以下问题：如果更新的开始日期与以前存在的更新的结束日期一致，则无法使用REST API为多个商店创建针对特殊价格的新计划更新。

<u>重现步骤</u>：

1. 设置其他网站、商店和商店视图。
1. 创建两个简单的产品：“product1”和“product2”。
1. 将product1分配给一个网站，将product2分配给两个网站。
1. 在ID为1的商店中，为商店视图上的product1的特殊价格创建计划更新。 使用以下有效负载将REST API `POST`请求用于`rest/V1/products/special-price`：
   `{        "prices": [            {                "price": 15,                "store_id": 1,                "sku": "product1",                "price_from": "2021-11-15 04:00:00",                "price_to": "2021-11-15 04:10:00"            }        ]    }`
1. 在对`rest/V1/products/special-price`使用以下有效负载的REST API `POST`请求（2}日期与上一个请求中的`price_to`日期相同）创建ID为1和2的商店视图上product2的特殊价格计划更新：`price_from`
   `{        "prices": [            {                "price": 14,                "store_id": 1,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            },            {                "price": 13,                "store_id": 2,                "sku": "product2",                "price_from": "2021-11-15 04:10:00",                "price_to": "2021-11-15 04:15:00"            }        ]    }`

<u>预期的结果</u>：

在两个商店视图上都创建了带特殊价格更改的计划更新。

<u>实际结果</u>：

Adobe Commerce引发错误。 未创建计划的更新。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
