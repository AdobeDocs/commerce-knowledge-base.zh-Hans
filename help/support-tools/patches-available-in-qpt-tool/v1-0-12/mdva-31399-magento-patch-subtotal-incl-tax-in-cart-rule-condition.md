---
title: '''MDVA-31399 patch：小计(包括 Tax)（在购物车规则条件中）'
description: MDVA-31399修补程序将添加*小计(包括 Tax)*选项更改为[购物车价格规则条件](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)，修复了无法根据小计应用购物车价格规则的问题(包括 税号。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。
exl-id: ea0f4060-753a-4b0d-896b-fff54ffd1a82
feature: Marketing Tools, Orders, Shopping Cart, Taxes
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-31399修补程序：小计(包括 Tax)（在购物车规则条件中）

MDVA-31399修补程序添加&#x200B;*小计(包括 税费)*&#x200B;选项到[购物车价格规则条件](https://docs.magento.com/user-guide/v2.3/marketing/price-rules-cart-create.html#step-2-describe-the-conditions)，修复了无法基于小计应用购物车价格规则的问题(包括 税号。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.2 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法应用基于小计的购物车价格规则(包括 税号。

<u>重现步骤</u>：

1. 配置产品价格以含税。
1. 创建20%的税则和税率。
1. 创建价格为&#x200B;**价格** = *100*&#x200B;的产品（此价格含税）。
1. 创建带有优惠券“10off”的新购物车价格规则，以便在小计符合以下条件时应用$10固定折扣：

**条件**： *如果所有这些条件均为TRUE：*        * **小计**&#x200B;等于或大于100。*

<u>预期的结果</u>：

能够创建带有优惠券的购物车小计价格规则，以将折扣应用于小计（包括税金）。

<u>实际结果</u>：

购物车规则条件中有两个选项：*小计*&#x200B;和&#x200B;*小计（不包括）。 税)*，无论选择哪项，该规则都只应用于不含税的小计。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
