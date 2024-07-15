---
title: 欧盟客户无法完成支付
description: 该文章修复了欧盟客户无法完成支付的问题。
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# 欧盟客户无法完成支付

该文章修复了欧盟客户无法完成支付的问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本
* Adobe Commerce内部部署2.2.x、2.3.x
* Magento Open Source2.2.x和2.3.x

## 问题

来自欧盟的顾客抱怨他们的信用卡交易被拒。

## 原因

欧盟使用更新版本[Directive2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN)修订了名为“支付服务指令(PSD)”的PSD。 这是一项欧盟(EU)指令，旨在管理整个欧盟和欧洲经济区(EEA)的支付服务和支付服务提供商。 强客户身份验证(SCA)是PSD2的一项要求，用于提高支付数据的安全性和身份验证。 如果您的支付解决方案不符合指令要求，这可能导致客户无法完成支付。 请在[相关的Adobe Commerce DevBlog文章](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460)中找到更多详细信息。

## 解决方案

遵循DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations)的[Adobe Commerce Payment Provider Recommendations部分的建议。
