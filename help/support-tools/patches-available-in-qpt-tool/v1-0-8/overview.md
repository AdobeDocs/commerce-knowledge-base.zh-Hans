---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.8'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.0.8中提供的修补程序所修复的问题。
exl-id: 6cd3eabe-067f-4e80-b17f-561290499261
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.8概述

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.0.8中提供的修补程序所修复的问题。

QPT v1.0.8包含以下修补程序：

1. **MDVA-28357**：将标准分析器替换为[!DNL ElasticSearch]索引中SKU字段的关键字令牌化器的自定义分析器，以使通配符搜索查询适用于包含连字符(“ — ”)的SKU。
1. **MDVA-29954**：修复了以下问题：*新的公司注册请求*&#x200B;和&#x200B;*您已链接到公司*&#x200B;电子邮件发自错误的地址。
1. **MDVA-30112**：修复了订单数超过&#x200B;*bunch-size*&#x200B;值的问题，Adobe Commerce将状态为&#x200B;*挂起*&#x200B;的订单视为不一致。
1. **MDVA-30963**：修复了产品筛选结果设置为仅包含为Admin中的&#x200B;*所有商店视图*&#x200B;范围指定的值的问题，该问题包含其值在商店视图级别被覆盖的产品。
1. **MDVA-31150**：修复了GETInvoice Rest API调用未返回商店信用卡余额和礼品卡余额的问题，当时，该发票通过Rest API调用过帐，并且订单由商店信用卡帐户和礼品卡帐户支付了一部分。
1. **MDVA-31242**：修复了[!UICONTROL Credit Memo]网格中显示错误货币符号的问题。
1. **MDVA-31295**：修复了在完成部分订购并对项目征税时未计算奖励点数的问题。

使用左侧的菜单导航到特定的修补程序页面。
