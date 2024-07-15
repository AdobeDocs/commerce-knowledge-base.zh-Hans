---
title: “MDVA-39935：GraphQL返回在网站级别禁用的可配置子产品”
description: MDVA-39935 Adobe Commerce修补程序修复了GraphQL返回在网站级别禁用的可配置子产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39935。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 45bd6bd9-3572-4477-a689-d6b952a3290a
feature: GraphQL, Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# MDVA-39935：GraphQL返回在网站级别禁用的可配置子产品

MDVA-39935 Adobe Commerce修补程序修复了GraphQL返回在网站级别禁用的可配置子产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39935。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使在网站级别禁用可配置的子产品后，GraphQL也会返回这些子产品。

<u>重现步骤</u>：

1. 在&#x200B;**商店** > **配置** > **目录** > **库存** > **库存选项** > **显示缺货产品** > **是**&#x200B;下启用显示缺货产品选项。
1. 选择具有两个以上&#x200B;**简单产品**&#x200B;的任意&#x200B;**可配置产品**。
1. 禁用&#x200B;**简单产品**&#x200B;并保存&#x200B;**可配置的产品**。
1. 使用GraphQL获取&#x200B;**可配置产品**&#x200B;数据。

<pre>
  <code class="language-graphql">
{
  products(filter: { sku: { eq: "cp1" } }) {
    items {
      __typename
      name
      sku
      ... on ConfigurableProduct {
        variants {
          product {
            __typename
            name
            sku
            color
            stock_status
          }
        }
      }
    }
  }
}
</code>
</pre>

<u>预期的结果</u>：

变体结果中未显示已禁用的产品。

<u>实际结果</u>：

在变量结果中获取禁用的产品数据。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Adobe Commerce质量修补程序的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
