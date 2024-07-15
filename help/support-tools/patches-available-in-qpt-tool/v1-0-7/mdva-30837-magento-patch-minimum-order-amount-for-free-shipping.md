---
title: 'MDVA-30837：免运费的最低订单金额'
description: MDVA-30837修补程序为免运费计算添加了配置选项，以便用户可以配置最低订单金额，以根据小计（或总计）获得免运费。 这允许对税务和配送方式进行本地自定义。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 64716d08-4ce0-40d5-aeb7-242e2aa85bb0
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# MDVA-30837：免运费的最低订单金额

MDVA-30837修补程序为免运费计算添加了配置选项，以便用户可以配置最低订单金额，以根据小计（或总计）获得免运费。 这允许对税务和配送方式进行本地自定义。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：**

* 云基础架构上的Adobe Commerce 2.3.1 - 2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修补程序MDVA-30837添加了配置设置，以将&#x200B;**最小订单金额**&#x200B;设置配置为基于小计（或总计）免费送货：

* 在免运费方法配置中&#x200B;**包括金额为**&#x200B;的税：*是/否*。
   * 当&#x200B;**含税金额**&#x200B;设置为&#x200B;*是*&#x200B;时，最小订单金额计算为小计+税 — 折扣。
   * 当&#x200B;**含税金额**&#x200B;设置为&#x200B;*否*&#x200B;时，最小订单金额计算为“小计 — 折扣”。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** >设置> **配置** > **销售** > **税**，并设置以下内容：

   * 基于&#x200B;*送货地址*&#x200B;的税费计算
   * 启用跨境贸易： *否*
   * 在目录中显示产品价格： *不含税*
   * 显示运费： *不含税*
   * 显示价格： *不含税*
   * 显示小计： *不包括税*
   * 显示运费金额： *不含税*
   * 显示礼品包装价格： *不含税*
   * 显示打印卡价格： *不含税*
   * 按订单总计包括税： *是*
   * 显示完整税务汇总： *是*

1. 转到&#x200B;**销售** > **送货设置** > **免运费**，并设置&#x200B;**最低订单金额** = *30*。
1. 转到&#x200B;**营销** >促销活动> **购物车价格规则**&#x200B;并创建新价格规则（有关详细步骤，请参阅用户指南中的[创建购物车价格规则](https://docs.magento.com/user-guide/marketing/price-rules-cart-create.html)）。

   * 优惠券代码= *特定优惠券*。
   * 条件：小计等于或大于$25。
   * 操作：免运费= *对于具有匹配物料的装运*。

1. 创建价格为$23.10的产品。
1. 将CA税添加到默认税则。
1. 将此产品添加到购物车。
1. 获取送货报价 — 税后，总计= 25.01美元，并且应用免运费。
1. 应用优惠券代码 — 它将不再有效，因为小计（不含税）为$23.10。

<u>预期的结果</u>：

在免运费方法配置中有额外的配置设置 — 包括税额的税： *是*/*否*：

* 当“包括税额至金额”设置为&#x200B;*是*&#x200B;时，最小订单金额按小计+税额 — 折扣计算。
* 当“包括税额至金额”设置为&#x200B;*否*&#x200B;时，最小订单金额计算为“小计 — 折扣”。

<u>实际结果</u>：

“免运费”价格规则条件只能基于“小计”，而“免运费”方法只能基于“总计”。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
