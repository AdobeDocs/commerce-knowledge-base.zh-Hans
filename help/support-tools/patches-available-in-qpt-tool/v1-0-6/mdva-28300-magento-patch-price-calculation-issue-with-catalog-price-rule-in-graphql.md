---
title: 'MDVA-28300：GraphQL中目录价格规则的价格计算问题'
description: MDVA-28300修补程序修复了GraphQL请求未反映目录价格规则中的价格更改的问题。 安装Quality Patches Tool (QPT) v.1.0.6后，即可使用此修补程序。 请注意，Adobe Commerce版本2.3.6中已修复此问题。
exl-id: 86079d29-db69-4758-a159-aeed8e0ea21f
feature: Catalog Management, GraphQL, Customer Service, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# MDVA-28300：GraphQL中目录价格规则的价格计算问题

>[!WARNING]
>
>名为MDVA-33975的新修补程序修复了GraphQL的价格计算问题。 MDVA-28300已弃用，建议您应用修补程序MDVA-33975。 要访问此修补程序，请参阅[MDVA-33975： GraphQL价格计算](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/mdva-33975-magento-patch-graphql-price-calculations.html)。

MDVA-28300修补程序修复了GraphQL请求未反映目录价格规则中的价格更改的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6时，此修补程序可用。 请注意，Adobe Commerce版本2.3.6中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本** Adobe Commerce内部部署2.3.5-p1创建的

**与Adobe Commerce版本兼容：** Adobe Commerce on-premsies和Adobe Commerce on cloud infrastructure 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将目录价格规则应用于特定客户组后，在GraphQL中无法正确计算购物车中的项目价格和订单总计。

<u>要再现的步骤：</u>

1. 创建新的客户帐户并将其Customer Group更改为Wrowsale。
1. 使用以下参数在&#x200B;**营销** > **促销活动** > **目录价格规则**&#x200B;中创建新目录规则：
   * 客户组： WriteralActions：
   * 应用：*应用为原始文件的百分比*
   * 折扣：*50*


1. 创建价格=100的新产品。
1. 使用之前创建的客户帐户登录到前端（如果您已经登录，请先注销，然后再登录）。
1. 将产品添加到购物车。 产品价格为50（正常价格100），订单合计：55（50 + 5发运成本）。
1. 执行我们的开发人员文档中的[customerCart query](https://devdocs.magento.com/guides/v2.3/graphql/queries/customer-cart.html)中描述的GraphQL API调用。

<u>预期结果：</u>

API和前端具有相同的订单总计，并且应用目录规则引入的折扣。

<u>实际结果：</u>

订单总计不应用目录规则折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [使用Quality Patches Tool](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)应用修补程序。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT中可用的修补程序一节。
