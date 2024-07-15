---
title: 直接配送选择错误的地址
description: 配送解决方案不选取产品来源的地址。
exl-id: ce89713f-d506-4e4f-bf49-cdee3e6d29b5
feature: Customer Service, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# 直接配送选择错误的地址

## 问题

配送解决方案不选取产品来源的地址。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce（所有版本），已安装Magento清单
* Adobe Commerce内部部署2.3.0及更高版本，安装了Magento清单
* 安装了Magento清单的Magento Open Source2.3.0及更高版本

### 原因

Magento清单当前不支持在结账期间使用基于源地址的直接发货率计算。 而是在所有情况下都使用配置中的默认存储地址。

## 相关阅读

* GitHub中的[Magento清单常见问题解答](https://github.com/magento/inventory/wiki/MSI-FAQs)。
