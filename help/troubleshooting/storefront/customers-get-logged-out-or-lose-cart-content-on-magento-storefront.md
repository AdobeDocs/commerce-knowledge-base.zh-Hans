---
title: 客户在Adobe Commerce店面被注销或丢失购物车内容
description: 此文章提供了针对此问题的解决方案和解决方法：在从支付或其他第三方服务（会话Cookie“丢失”）重定向回Adobe Commerce商店后，客户被注销或从店面购物车中丢失商品。
exl-id: 9175570c-b06c-4a65-b8ca-7a12ff266afb
feature: Orders, Page Content, Shopping Cart, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# 客户在Adobe Commerce店面被注销或丢失购物车内容

本文针对以下问题提供了解决方案：在从支付或其他第三方服务（会话Cookie“丢失”）重定向回Adobe Commerce商店后，客户注销或从店面购物车中丢失商品。

## 受影响的产品和版本

* Adobe Commerce内部部署，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)
* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

<u>要再现的步骤：</u>

1. 客户将产品添加到店面的购物车，然后进行结账。
1. 客户将被重定向到第三方地点，以进行付款/运输或其他信息/服务。
1. 客户将被重定向回商店。

<u>实际结果：</u>

客户已重定向到空的购物车或空白页面。

<u>预期结果：</u>

客户重定向到成功付款页面（或其他成功页面），并且没有丢失结账数据和进度。

## 原因

SameSite Cookie属性设置为&#x200B;*Lax*&#x200B;或未指定（被视为设置为&#x200B;*Lax*）。 拥有`SameSite` = *Lax*&#x200B;将禁止通过`POST`请求将Cookie传输到外部URL。

## 解决方案

要解决此问题，请联系第三方服务提供商，并请求其开发人员更新其集成以配置Cookie参数。

## 相关阅读

[Chrome SameSite更新](https://www.chromestatus.com/feature/5088147346030592)
