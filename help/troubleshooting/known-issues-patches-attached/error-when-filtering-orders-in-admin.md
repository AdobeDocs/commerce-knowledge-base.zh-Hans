---
title: 在管理员中过滤订单时出错
description: 本文为Adobe Commerce问题提供了一个修补程序，在该问题中，尝试按日期在管理员中过滤订单时出现错误，显示消息“完整性约束违规1052 Column 'created_at' where子句不明确”。
feature: Orders
role: Developer
source-git-commit: e5eb65b23afaed4658f8576c747f11a31a8ec1aa
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 在管理员中过滤订单时出错

本文为Adobe Commerce问题提供了一个修补程序，该问题导致在尝试按日期筛选管理员中的订单时出现错误，并显示消息： *完整性约束违规： 1052列“created_at”，其中where子句不明确*。

## 受影响的版本

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7

## 问题

在管理员中按日期过滤订单会返回错误。

exception.log显示：

```SQL
report.CRITICAL: PDOException: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'created_at' in where clause is ambiguous in /path/to/magento/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
```

<u>要再现的步骤：</u>

1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
   * 在网格中设置&#x200B;**[!UICONTROL Purchase Date Ascending]**&#x200B;顺序，或
   * 在筛选器中设置&#x200B;**[!UICONTROL Purchase Date Filter]**。

1. 出现错误： *处理默认视图时出现问题，我们已将该筛选器还原到其原始状态。*

## 原因

[!DNL PayPal Braintree]模块有问题。

## 解决方案

要解决此问题，请应用本文附带的修补程序。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[bundle_3357_filter_order_in_admin_by_date_patch.zip](assets/bundle-3357-unable-to-filter-order-in-admin-by-date.zip)

该修补程序与所有受影响的版本和版本兼容。

## 如何应用修补程序

有关说明，请参阅支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
