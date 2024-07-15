---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.7'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.0.7中提供的修补程序所修复的问题。
exl-id: 2415ca7a-4aec-4a63-9ae9-ee7b29bbc8d7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.7概述

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.0.7中提供的修补程序所修复的问题。

QPT v1.0.7包含以下修补程序：

1. **MDVA-29148**：修复了在通过API调用创建产品时，如果有效负载中未提供值，则`\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend`（如Multiselect）类型的产品自定义属性不使用其默认值。
1. **MDVA-29389**：修复了“高级报告”的问题，其中`analytics_collect_data` cronjob显示： *端口必须在主机参数（如localhost：3306）*&#x200B;中进行配置。
1. **MDVA-30594**：修复了在配置FPT时签出期间无法保存具有多个地址的订单的问题。
1. **MDVA-30782**：修复了在不考虑购物车规则的情况下显示动态块的问题。
1. **MDVA-30815**：修复了在更改搜索结果页面上应显示多少搜索结果时的问题。
1. **MDVA-30837**：为免运费计算添加了配置选项，以便用户能够配置最低订单金额，以根据小计（或总计）获得免运费。
1. **MDVA-30945**：修复了在更新购物车`Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`时收到致命错误消息的问题。
1. **MDVA-30972**：修复了在使用WebApi创建部分装运后，自定义订单状态更改为&#x200B;*正在处理*&#x200B;的问题。
1. **MDVA-31007**：修复了“我的帐户”区域和后端的“订单详细信息”页面中未正确显示自定义地址属性的问题。
1. **MDVA-31021**：修复了`module-catalog-import-export/Model/Import/Product/Option.php`中存在性能问题的问题。 如果`catalog_product_option`表中的记录数超过~100,000条，则验证单个产品的新CSV所花费的时间将少于10秒。
1. **MDVA-31224**：改进捆绑产品的`catalog_product_price`重新索引操作的性能。
1. **MDVA-31282**：修复了Adobe Commerce中[!DNL Paypal PayFlow Pro]上发生双重授权的问题。 双重授权还会产生绕过[!DNL PayFlow Pro's]欺诈筛选器和交易费用翻倍的效果。
1. **MDVA-31343**：修复了在计划类别时已删除的正文类`page-layout-category-full-width`的问题。

使用左侧的菜单导航到特定的修补程序页面。
