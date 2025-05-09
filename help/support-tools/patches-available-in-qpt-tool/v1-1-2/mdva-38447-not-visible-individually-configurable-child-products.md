---
title: 'MDVA-38447：GraphQL响应中返回“不可见”可单独配置的子产品，导致MySQL查询缓慢'
description: MDVA-38447 Adobe Commerce修补程序修复了以下问题：GraphQL响应中返回“不可见”可单独配置的子产品，以及使用类别过滤器的GraphQL产品查询MySQL速度缓慢。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-38447。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 302e7458-d9ea-466a-a2ac-d86a8ee3eca3
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-38447：GraphQL响应中返回“不可见”可单独配置的子产品，导致MySQL查询缓慢

MDVA-38447 Adobe Commerce修补程序修复了以下问题：GraphQL响应中返回“不可见”可单独配置的子产品，以及使用类别过滤器的GraphQL产品查询MySQL速度缓慢。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-38447。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL响应中返回“不可见”可单独配置的子产品，并且使用类别过滤器降低GraphQL产品查询的MySQL查询速度。

<u>先决条件</u>：

必须安装B2B模块。

<u>重现步骤</u>：

1. 创建简单产品设置为&#x200B;**不可单独显示的产品**。
1. 运行&#x200B;**完整重新索引**。
1. 运行&#x200B;**GraphQL查询**，如下所示：

<pre>查询getFilteredProducts(
  $filter： ProductAttributeFilterInput！
  $sort： ProductAttributeSortInput！
  $search：字符串
  $pageSize： Int！
  $currentPage： Int！
) &lbrace;
  products(
    过滤器：$filter
    排序：$sort
    搜索：$search
    pageSize：$pageSize
    currentPage：$currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    项目&lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

变量：

<pre>{"filter"：{"user_group"：{"eq"："}}，"search"："config-100"，"sort"：{}，"pageSize"：200，"currentPage"：1}
</pre>

<u>预期的结果</u>：

在响应中将不返回可见性设置为“单独不可见”的产品。

<u>实际结果</u>：

作为响应，将返回其可见性设置为“单独不可见”的产品。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Adobe Commerce质量修补程序的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修补程序部分。
