---
title: 'MDVA-31295：部分订单的会员积分'
description: MDVA-31295修补程序修复了在完成部分订单并对项目征税时，无法正确计算奖励点的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 10e8a3a9-bfab-4256-b772-fd64e8885da3
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31295：部分订单的会员积分

MDVA-31295修补程序修复了在完成部分订单并对项目征税时，无法正确计算奖励点的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce内部部署2.3.0

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当订单完成（部分发运）并且项目已征税时，不会将奖励应用于客户的帐户。 当商品不征税时，奖励将成功添加到客户的账户中。

<u>重现步骤</u>：

1. 以客户身份登录storefront。
1. 将两个产品添加到购物车。
1. 前往结帐、设置含税的配送地址并下订单。
1. 在管理员中，转到最近下单的订单。
1. 单击&#x200B;**发票**&#x200B;并将其中一个项目的&#x200B;**数量设置为发票**&#x200B;设置为0，然后单击&#x200B;**更新数量**。 提交发票。
1. 单击“发运”并将未开票的项目的&#x200B;**数量设置为“发运**”设置为0。 单击&#x200B;**提交装运**。
1. 单击取消订单。 状态将设置为“完成”。
1. 在管理员中，转到&#x200B;**客户** >选择客户购买早于> **奖励积分** > **奖励积分历史记录**。
1. 检查所下订单获得的奖励积分。

<u>预期的结果</u>：

当部分订单完成时，应计算应纳税订单的奖励积分。

<u>实际结果</u>：

部分订单完成时，不会计算应纳税订单的奖励积分。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
