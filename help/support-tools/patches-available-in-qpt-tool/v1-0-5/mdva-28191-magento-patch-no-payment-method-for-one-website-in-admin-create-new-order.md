---
title: 'MDVA-28191：管理员创建新订单中一个网站没有付款方式'
description: MDVA-28191修补程序修复了以下问题：某个网站的管理员**创建新订单**中未加载付款方法，尽管可能显示其他网站的付款方法。  安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版后，即可使用此修补程序。
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191：管理员创建新订单中一个网站没有付款方式

MDVA-28191修补程序修复了在管理员&#x200B;**新建订单**&#x200B;中没有为某个网站加载付款方法的问题，尽管可能为其他网站显示了付款方法。  安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版时，此修补程序可用。

## 受影响的产品和版本

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.3到2.4.1（包括2.3.5-p1）。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从后端Adobe Commerce创建订单时，会创建两个报价，一个处于不活动状态，另一个处于活动状态。 但会话包含不活动的报价ID。

<u>重现步骤</u>

1. 转到&#x200B;**管理员面板** > **销售** > **订单**，然后单击&#x200B;**创建新订单**&#x200B;按钮。
1. 选择要为其创建订单的客户。
1. 如果您的商店有多个视图，请在&#x200B;**新建订单**&#x200B;页面上为您选择的用户选择下达订单的商店视图。
1. 从&#x200B;**客户的“活动”**&#x200B;部分添加产品，或单击&#x200B;**“添加产品”**&#x200B;从目录添加产品。 向下滚动页面以完成订单所需的以下部分：
   * 应用优惠券代码
   * 付款方式
   * 配送方式
   * 订单备注

<u>预期结果：</u>

应在管理员中加载所有网站的支付方式。

<u>实际结果：</u>

此网站没有可用的付款方法（也不显示消息“*无需付款信息*”），但在测试其他网站的订单时可能会显示付款方法。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
