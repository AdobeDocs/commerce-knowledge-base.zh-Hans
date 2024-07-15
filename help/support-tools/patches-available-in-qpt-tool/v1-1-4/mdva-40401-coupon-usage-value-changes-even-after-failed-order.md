---
title: 'MDVA-40401：订单失败后优惠券使用值发生更改'
description: MDVA-40401修补程序修复了即使在订单失败后优惠券使用值也会更改的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4后，即可使用此修补程序。 修补程序ID为MDVA-40401。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: c497ee84-9c20-4c75-ad3a-3b71f699acbf
feature: Orders
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40401：订单失败后优惠券使用值发生更改

MDVA-40401修补程序修复了即使在订单失败后优惠券使用值也会更改的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-40401。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.6 - 2.3.7-p2、2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户以失败顺序使用优惠券后，将无法重新应用优惠券。

<u>重现步骤</u>：

1. 使用自动生成的优惠券创建购物车规则。
1. 将产品添加到购物车并应用优惠券。
1. 转到&#x200B;**签出**。
1. 下订单前，使添加的产品“缺货”。
1. 您应会收到&#x200B;*缺货*&#x200B;错误。
1. 运行cron。
1. 转到购物车并移除该产品。
1. 添加其他产品并应用优惠券。

<u>预期的结果</u>：

由于未下前一个订单，因此优惠券代码应成功应用。

<u>实际结果</u>：

您收到的&#x200B;*优惠券代码无效*&#x200B;错误。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
