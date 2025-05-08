---
title: 客户组名称、区段和促销规则信息通过 [!DNL GraphQL]公开
description: 本文提供了一个修补程序，以防止客户组名称、客户区段和促销规则信息通过 [!DNL GraphQL]泄露。
feature: GraphQL
role: Admin, Developer
source-git-commit: f32085c80c9dbce513dad15ebf5f77a0e6398466
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# 通过[!DNL GraphQL]公开的客户组名称、区段和促销规则信息

本文提供了一个修补程序，以防止客户组名称、客户区段和促销规则信息通过[!DNL GraphQL]公开。 Adobe Commerce 2.4.8-p1中计划修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8

## 问题

对于[!UICONTROL Storefront Personalization Drop-ins]，引入了新的[!DNL GraphQL]变动，以显示客户组名称、区段、购物车和目录规则等基本信息。 但是，如果名称中包含敏感数据（如优惠详细信息或优惠券代码），则可能会泄露。

### 重现问题的步骤

#### 案例I：[!UICONTROL Catalog Rule]

1. 在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**。
1. 定义规则条件（例如，产品属性或类别）。
1. 保存并应用规则。
1. 确保产品符合规则条件。
1. 运行以下[!DNL GraphQL]查询以获取所有规则：

   ```
   query {
       allCatalogRules {
           name
       }
   }
   ```

1. 查询产品以验证规则是否适用：

   ```
   query {
       products(filter: { sku: { eq: "product-sku" } }) {
           items {
               name
               rules {
                   name
               }
           }
       }
   }
   ```

#### 案例II： [!UICONTROL Cart Rule]

1. 在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rule]** > **[!UICONTROL Add New Rule]**。
1. 设置条件，如最小购物车值和客户组。
1. 保存并应用规则。
1. 将产品添加到购物车以触发规则。
1. 使用[!DNL GraphQL]验证所有购物车规则：

   ```
   query {
       allCartRules {
           name
       }
   }
   ```

1. 检查规则是否已应用于活动的购物车：

   ```
   query {
       cart(cart_id: "your-cart-id") {
           rules {
               name
           }
       }
   }
   ```

#### 案例III： [!UICONTROL Customer Group]

1. 在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Customer Groups]**。
1. 验证预期的组是否存在。
1. 使用[!DNL GraphQL]获取所有组：

   ```
   query {
       allCustomerGroups {
           name
       }
   }
   ```

1. 验证客户/来宾的组：

   ```
   query {
       customerGroup {
           name
       }
   }
   ```

#### 案例IV： [!UICONTROL Customer Segment]&#x200B;(仅适用于Adobe Commerce)

1. 在&#x200B;*管理员*&#x200B;侧边栏上，转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Customer Segments]** → **[!UICONTROL Add Segment]**。
1. 定义基于客户的条件（例如，订单、购物车内容）。
1. 分配适用的范围： *[!UICONTROL Visitor]*、*[!UICONTROL Registered]*&#x200B;或两者。
1. 确保条件与测试客户匹配。
1. 使用[!DNL GraphQL]检查所有区段：

   ```
   query {
       allCustomerSegments {
           name
           apply_to
       }
   }
   ```

1. 验证应用于购物车的区段：

   ```
   query {
       customerSegments(cartId: "your-cart-id") {
           name
       }
   }
   ```

<u>预期的结果</u>：

客户组、区段和促销规则信息的名称不通过[!DNL GraphQL]公开。

<u>实际结果</u>：

客户组、区段和促销规则信息的名称通过[!DNL GraphQL]公开。

## 解决方案

根据您的Adobe Commerce版本应用附加的修补程序：

* 对于Adobe Commerce版本2.4.8：

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
   * [LYNX-839_EE_2.4.8.patch](assets/LYNX-839_EE_2.4.8.patch.zip)

* 对于[!DNL Magento]，打开Source版本2.4.8：

   * [LYNX-839_CE_2.4.8.patch](assets/LYNX-839_CE_2.4.8.patch.zip)
