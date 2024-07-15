---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.0.5'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.0.5中提供的修补程序所修复的问题。
exl-id: 439358e8-d6bc-4d35-aee1-f4fc33ae267c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# [!DNL Quality Patches Tool] (QPT) v1.0.5概述

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.0.5中提供的修补程序所修复的问题。

QPT v1.0.5包含以下修补程序：

1. **MDVA-28191**：修复了在通过管理员创建订单期间未加载任何付款方法的问题。
1. **MDVA-28409**：修复了数据库中过期的引号数量巨大时，`sales_clean_quotes` cron作业失败并出现&#x200B;*内存不足*&#x200B;错误的问题。
1. **MDVA-28661**：修复了在更改公司管理员后，“公司用户”公司帐户部分引发错误的问题。
1. **MDVA-28763**：修复了在使用REST API多次更新产品信息后产品图像重复的问题。
1. **MDVA-29042**：修复了在将新产品添加到共享目录后目录权限自动更改为&#x200B;*允许*&#x200B;的问题。
1. **MDVA-29959**：修复了具有&#x200B;*公司*&#x200B;权限的受限管理员用户不允许删除公司帐户的问题。
1. **MDVA-30107**：修复了在将不同的基本URL用于商店视图时，商店切换器无法按预期工作的问题。
1. **MDVA-30265**：修复了在创建发票后装运跟踪链接停止工作的问题。
1. **MDVA-30284**：修复了目录搜索索引器由于以下&#x200B;*[!DNL Elasticsearch]错误而失败的问题：已超过索引中字段总数的限制。*
1. **MDVA-30428**：修复了将产品分配给自定义库存源时，客户无法将产品添加到愿望清单的问题。
1. **MDVA-30593**：修复了根据“报价生存期”设置过期的报价未清除的问题。

使用左侧的菜单导航到特定的修补程序页面。
