---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.13'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.0.13中提供的修补程序所修复的问题。
exl-id: c25d2926-2137-4a55-abb2-8c0cbff184c9
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.13概述

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.0.13中提供的修补程序所修复的问题。

QPT v1.0.13包含以下修补程序：

1. **MCP-87**：改进了大型配置文件的类别产品和库存索引器的索引时间。
1. **MDVA-13203**：修复了在完全重新索引后出现&#x200B;*完整性约束冲突search_tmp_ table*&#x200B;错误的问题。
1. **MDVA-19391**：修复了`catalog_category_entity_text`表中由于NULL描述记录而`analytics_collect_data`引发错误的问题。
1. **MDVA-20376**：修复了在下单后登录的客户在`exception.log`中&#x200B;*没有客户识别码= 1*&#x200B;的此类实体错误的问题。
1. **MDVA-22150**：修复了以下问题：如果在Admin中禁用了可配置产品，则购物车中具有可配置产品且应用了优惠券的客户无法登录。
1. **MDVA-23426**：修复了Adobe Commerce发送的通知电子邮件包含空白正文并将内容添加为附件的问题。
1. **MDVA-23764**：修复了`JsFooterPlugin.php`中影响动态块显示的错误。
1. **MDVA-30858**：修复了&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL PayPal]**&#x200B;结算下无法按预期提供[!DNL PayPal]结算报告的问题。
1. **MDVA-32545**：修复了在从管理员创建订单时未自动发送发票的问题。
1. **MDVA-32714**：修复了客户组价格在GraphQL产品查询中无效的问题。
1. **MDVA-33106**：修复了在执行cron `run`命令后擦除重新计划的产品更改的问题。

使用左侧的菜单导航到特定的修补程序页面。
