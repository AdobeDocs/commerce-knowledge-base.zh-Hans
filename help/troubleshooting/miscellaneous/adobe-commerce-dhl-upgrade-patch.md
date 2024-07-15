---
title: 应用修补程序以继续将DHL作为运输运营商
description: 本文提供了一个修补程序，允许使用Adobe Commerce 2.4.4及更早版本的商家在DHL架构6.0于2022年7月底至9月被弃用后继续提供DHL交付。
exl-id: 4350e83a-495b-41b4-a526-dae5923e9d41
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# 应用修补程序以继续将DHL作为运输运营商


## 受影响的产品和版本

* Adobe Commerce 2.4.4及更早版本，所有部署方法。

## 问题

DHL正在引入6.2架构版本，并在2022年7月底 — 9月底之前弃用版本6.0。 Adobe Commerce 2.4.4及更早版本的DHL集成仅支持版本6.0。

## 解决方案

计划于2022年8月发布的Adobe Commerce 2.4.5将包含使用版本6.2架构与DHL的升级集成。 在新版本发布之前（或者如果您选择不升级），我们建议您应用AC-3022修补程序，实施6.2版本的DHL模式支持，以便在弃用后继续在您的商店中提供DHL送货服务。

## Patch

修补程序ID为AC-3022，可在Quality Patches Tool版本1.1.16中找到。
有关如何使用QPT和安装修补程序的信息，请参阅开发人员文档中的[Quality Patches Tool (QPT) > Usage](https://devdocs.magento.com/quality-patches/usage.html)一文。

该修补程序适用于以下Adobe Commerce版本：

* 2.4.0 - 2.4.4-p1
* 2.3.7

## 相关阅读

* 我们用户指南中的[配送公司> DHL](https://docs.magento.com/user-guide/shipping/dhl.html)
* 我们用户指南中的[投放方法](https://docs.magento.com/user-guide/configuration/sales/delivery-methods.html)
