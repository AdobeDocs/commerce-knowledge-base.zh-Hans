---
title: 'MDVA-44562：默认商店ID覆盖的报价单项目的商店ID'
description: MDVA-44562修补程序修复了以下问题：对于GraphQL请求，默认商店ID将覆盖报价项的商店ID。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16后，即可使用此修补程序。 修补程序ID为MDVA-44562。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: 902bfc05-411d-4a6c-a6e8-cd7376629b0c
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44562：由默认存储ID覆盖的报价单项目的存储ID

MDVA-44562修补程序修复了以下问题：对于GraphQL请求，默认商店ID将覆盖报价项的商店ID。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.16后，即可使用此修补程序。 修补程序ID为MDVA-44562。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

报价项目的商店ID将被GraphQL请求的默认商店ID覆盖。

<u>重现步骤</u>：

1. 创建新的商店视图。
1. 为每个商店视图创建具有不同名称的新简单产品。
1. 创建新客户。
1. 获取客户授权令牌。

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. 使用授权令牌为客户创建新报价。

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. 将产品添加到购物车。

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. 获取默认商店视图的购物车内容。

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. 获取新商店视图的购物车内容。

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>预期的结果</u>：

来自新商店视图的响应显示来自新商店视图的产品名称。

<u>实际结果</u>：

来自新商店视图的响应在默认商店视图下显示产品名称设置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
