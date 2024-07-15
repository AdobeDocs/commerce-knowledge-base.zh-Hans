---
title: 'MDVA-38270：客户订单合计中缺少礼品卡金额'
description: MDVA-38270修补程序修复了在客户订单总计中找不到礼品卡金额的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25后，即可使用此修补程序。 修补程序ID为MDVA-38270。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 4ab315c4-d26e-4270-a556-66601d01fb2e
feature: Gift, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# MDVA-38270：客户订单合计中缺少礼品卡金额

MDVA-38270修补程序修复了在客户订单总计中找不到礼品卡金额的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25时，此修补程序可用。 修补程序ID为MDVA-38270。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
云基础架构上的Adobe Commerce 2.4.2-p1

**与Adobe Commerce版本兼容：**
Adobe Commerce（所有部署方法） 2.4.1-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

订单总计响应中缺少礼品卡金额。

<u>先决条件</u>：

1. 创建客户帐户。
1. 使用礼品卡下订单（礼品卡覆盖整个订单）。

<u>重现步骤</u>：

对客户、订单、物料、合计进行客户查询：

```GraphQL
query {
  customer {
    orders(
      pageSize: 20
    ) {
      items {
        id
        order_date
        total {
          grand_total {
            value
            currency
          }
          total_giftcard {
              applied_balance {
                value
                currency
              }
              code
              current_balance {
                value
                currency
              }
              expiration_date
          }
        }
        status
      }
    }
  }
}
```

<u>预期的结果</u>：

`total_giftcard`字段可用。

<u>实际结果</u>：

没有可用的礼品卡相关字段。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
