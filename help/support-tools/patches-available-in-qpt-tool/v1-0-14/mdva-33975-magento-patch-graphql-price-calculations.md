---
title: 'MDVA-33975修补程序：GraphQL价格计算'
description: “MDVA-33975修补程序修复了GraphQL价格计算问题。 这些问题包括：
exl-id: a8266334-72cb-4b50-9ff5-9a977d762e5c
feature: GraphQL, Customer Service, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# MDVA-33975修补程序：GraphQL价格计算

MDVA-33975修补程序修复了GraphQL价格计算问题。 这些问题包括：

* 将目录价格规则应用于特定客户组时，在GraphQL中无法正确计算购物车中的商品价格和订单总计。
* 目录价格规则未包含在API的`CartItemPrices`中。
* GraphQL产品查询响应中未添加一般客户的客户组价格。
* 在就报价价格作出回应之前重新计算报价总额会导致应用的规则丢失。
* 在上一个开票步骤中未检索到运费折扣，并且显示的总计不正确。
* 在购物车价格规则条件中使用客户区段时，不会在GraphQL中应用折扣。

安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.14时，此修补程序可用。

## 受影响的产品和版本

* 该修补程序是为Adobe Commerce内部部署2.4.1而设计的。
* 该修补程序还与以下Adobe Commerce版本兼容：Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.4 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
