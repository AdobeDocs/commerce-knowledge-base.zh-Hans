---
title: Adobe Commerce 2.4.0已知问题：Klarna缺少“退款”标签
description: 本文为管理员中缺少**Refute**标签（供应商捆绑扩展）的已知问题提供了解决方法。 当在Klarna门户网站进行退款时，已退款的捆绑产品旁边不显示**退款**标签。
exl-id: f08039b2-7f8b-481e-8ec8-1659e227744f
feature: B2B, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Adobe Commerce 2.4.0已知问题：Klarna缺少“退款”标签

本文为管理员中缺少Klarna VBE（供应商捆绑扩展）中的&#x200B;**退款**&#x200B;标签的已知问题提供了解决方法。 在Klarna门户中进行退款时，**退款**&#x200B;标签不显示在已退款的捆绑产品旁边。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.0
* 云基础架构上的Adobe Commerce 2.4.0

## 问题

<u>先决条件：</u>

* Klarna已启用。
* 将创建捆绑产品。

<u>重现步骤</u>

1. 转到Adobe Commerce前端，并将捆绑产品添加到&#x200B;**购物车**。
1. 导航到签出。
1. 将使用者信息输入到结帐中，然后单击&#x200B;**下一步**。
1. 选择&#x200B;**KP选项**&#x200B;并单击&#x200B;**下单**。
1. 转到&#x200B;**管理员** > **销售** > **订单**。
1. 打开订单。
1. 为产品创建发票。
1. 转到&#x200B;**发票** > **选择发票** >单击&#x200B;**贷项通知单** >单击&#x200B;**退款** （不是&#x200B;**离线退款**）。
1. 去克拉纳的门户。
1. 打开订单。
1. 存在&#x200B;**退款**&#x200B;标签。

<u>预期的结果</u>

在Klarna门户上，**退款**&#x200B;标签显示在已退款的产品旁边。

<u>实际结果</u>

在Klarna门户上，**退款**&#x200B;标签未显示在已退款的产品旁边。

## 解决方法

此问题的解决方法是忽略Klarna门户中缺少的已退款捆绑产品的&#x200B;**退款**&#x200B;标签。 已退款，即使未显示&#x200B;**退款**&#x200B;标签也是如此。 Adobe Commerce 2.4.1预计将于2020年第4季度发布，可修复此问题。

## 我们的支持知识库中的相关读物：

* [Adobe Commerce 2.4.0已知问题：Braintree支付方法未出现在多地址结账中](/help/troubleshooting/payments/magento-2-4-0-braintree-not-in-multiple-addresses-checkout.md)
* [Adobe Commerce 2.4.0已知问题：在结账期间为某些国家/地区显示选择本地支付方法的错误消息](/help/troubleshooting/payments/magento-2-4-0-checkout-error-selecting-local-payments.md)
