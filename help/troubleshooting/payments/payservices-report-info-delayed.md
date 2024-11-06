---
title: 延迟支付服务报表数据
description: 本文解释了为什么支付服务中的报表数据可能会延迟。
exl-id: 2f3249d1-be12-45bc-aa73-bef9766509ae
feature: Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 延迟支付服务报表数据

本文解释了为什么支付服务中的报表数据可能会延迟。

## 受影响的产品和版本

* [Payment Services](https://marketplace.magento.com/magento-payment-services.html)现在与Adobe Commerce版本2.4.0到2.4.4兼容。

## 问题

付款和订单付款状态报表的Payment Services报表数据可能不会立即同步。

例如，在您开票（捕获）订单或发出订单的贷项通知单之后，订单的状态可能无法立即使用。

<u>重现步骤</u>：

前提条件：使用“付款服务”功能下达订单。

1. 在[管理员](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin)中，订单已开票[](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice) （或[已取消](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order)或通过贷项通知单](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos)退款[）。
1. 定位至“订单付款状态”报表，以查看有关该订单的信息。
1. 状态显示为`AUTHORIZED`，这是开票或其他订单操作之前的订单状态。

   Commerce尚未同步数据并将其发送到Payment Services，因此报表尚未识别新订单状态。

>[!NOTE]
>
>这只是一个常见用例。 当发生[订单操作](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/orders#actions)并且数据在适用的报表中不可立即使用时，可能会出现其他用例。

<u>预期的结果</u>：
在对订单执行操作后，将立即填充报表数据。

<u>实际结果</u>：
刚刚完成的订单操作的可见报表数据可能会延迟。 付款报告可能会延迟24-48小时。 订单付款状态报告可能会延迟几小时。

## 原因

有两个因素会影响“管理员”中可见数据的延迟：

* 您选择通过Admin](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/configure-admin.html)中的[配置从Commerce同步（导出和保留）数据的频率。
* PayPal发布报表数据的时间范围。

## 解决方案

对于订单付款状态报表：

1. 导航到&#x200B;**销售** > **付款服务**。
1. 单击&#x200B;**订单付款状态**&#x200B;查看订单付款状态报表表。
1. 通过单击报表表格右上角的&#x200B;**强制重新同步**&#x200B;图标，强制重新同步。
1. 您应会看到报表表中上次更新的时间戳更改和新加载的事务。

对于PayPal支付报告而言，由于依赖于PayPal的数据发布时间范围，预计结果将延迟24至48小时。
