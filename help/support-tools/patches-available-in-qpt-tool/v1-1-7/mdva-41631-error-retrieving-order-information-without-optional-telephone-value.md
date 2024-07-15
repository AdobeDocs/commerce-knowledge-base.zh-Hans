---
title: '''MDVA-41631：检索订单信息时出错，没有可选的“电话”值'
description: MDVA-41631修补程序修复了以下问题：用户通过GraphQL检索订单信息时，若没有可选的“电话”值，则会出现错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 94b0b918-c1f9-4f5d-8fcd-8b92a9ca8c59
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-41631：检索没有可选“电话”值的订单信息时出错

MDVA-41631修补程序修复了以下问题：用户通过GraphQL检索订单信息时，若没有可选的“电话”值，则会出现错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7时，此修补程序可用。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户通过GraphQL检索订单信息时，如果没有可选的“telephone”值，则会收到错误。

<u>重现步骤</u>：

1. 前往&#x200B;**商店** > **配置** > **客户** > **客户配置** > **名称和地址选项** > **显示电话**&#x200B;并将电话号码设置为可选。
1. 使用GraphQL API作为登录客户下订单。
   * 设置帐单和送货地址时，请勿设置电话号码。 按照开发人员文档中的[GraphQL结帐教程](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html)中提供的说明进行操作。
1. 使用GraphQL [customerOrders查询](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html)检索订单。

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>预期的结果</u>：

用户获取订单信息。

<u>实际结果</u>：

用户收到以下错误： *&quot;message&quot;：&quot;Internal server error&quot;，*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
