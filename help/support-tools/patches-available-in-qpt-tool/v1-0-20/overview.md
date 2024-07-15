---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.20'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.0.20中提供的修补程序所修复的问题。
exl-id: 13ed85f9-4ecb-467f-9ed0-ceec4ac200db
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.20概述

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.0.20中提供的修补程序所修复的问题。

QPT v1.0.20包含以下修补程序：

1. **MC-41359**：修复了SameSite Cookie参数设置不正确的问题。
1. **MDVA-11189**：修复了在导入CSV文件以更新产品库存后，`cataloginventory_stock`表中的行被删除的问题。
1. **MDVA-15546**：修复了在创建订单后，异常日志中显示&#x200B;*Column entity_id where子句不明确*&#x200B;错误的问题。
1. **MDVA-19640**：修复了[!DNL Advanced Reporting]未显示任何数据的问题。
1. **MDVA-21095**：修复了在批量属性值更新后查询`INSERT INTO search_tmp`无法结束的问题。
1. **MDVA-22026**：修复了从CSV文件导入产品（包括来自外部URL的图像）失败的问题。
1. **MDVA-22383**：修复了保存产品需要很长时间且页面会中断的问题。
1. **MDVA-23845**：修复了在启用JavaScript缩小后无法预览电子邮件模板的问题。
1. **MDVA-26639**：修复了在创建新的订单确认电子邮件模板时，订单邮件中缺少订单项的问题。
1. **MDVA-33168**：修复了通过API更新产品属性时，所有其他属性都更改为空值的问题。
1. **MDVA-36170**：通过使用类别缓存标记，修复了GraphQL查询未缓存的问题。

使用左侧的菜单导航到特定的修补程序页面。
