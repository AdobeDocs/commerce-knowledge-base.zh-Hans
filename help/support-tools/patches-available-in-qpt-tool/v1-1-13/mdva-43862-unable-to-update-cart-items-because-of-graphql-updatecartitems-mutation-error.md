---
title: “MDVA-43862：由于GraphQL UpdateCartItems突变错误，客户无法更新购物车项目”
description: MDVA-43862修补程序解决了由于GraphQL UpdateCartItems突变错误而导致客户无法更新购物车项目的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43862。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 5f0a2970-34a8-4a25-baf8-15c007f97084
feature: GraphQL, Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43862：由于GraphQL UpdateCartItems突变错误，客户无法更新购物车项目

MDVA-43862修补程序解决了由于GraphQL UpdateCartItems突变错误而导致客户无法更新购物车项目的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43862。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法）2.4.3-p1、2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于GraphQL UpdateCartItems突变错误，客户无法更新购物车项目。

<u>重现步骤</u>：

1. 通过指定一个简单的(MH01-XL-Gray)来创建可配置产品(MH01)。
1. 转到Commerce管理员> **目录** > **产品** > **SKU** > **MH01** > **可自定义选项**。
1. 向产品添加自定义选项。
   * 选项标题：选项1
   * 选项类型：字段
   * 必需：是
   * 价格：10.00
   * 价格类型：固定
   * SKU： MHC1
   * 最大字符数：25
1. 运行以下GraphQL查询以生成购物车ID。

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. 记下购物车ID代码。
1. 运行以下查询以将可配置产品添加到购物车：

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. 您会注意到购物车中填充了可配置项目。
1. 记下返回的uid。
1. 再次运行以下查询以更新购物车项目。

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. 观察响应。

<u>预期的结果</u>：

购物车已更新，且没有出现任何问题。

<u>实际结果</u>：

您会收到以下错误：

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
