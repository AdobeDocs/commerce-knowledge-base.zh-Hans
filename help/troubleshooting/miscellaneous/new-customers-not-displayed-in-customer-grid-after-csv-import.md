---
title: CSV导入后，新客户未显示在客户网格中
description: 修复了从“.csv”文件导入后，在**Customers** &amp；gt； **All customers**下看不到新客户的问题。 解决方案是将“customer_grid”索引器设置为“保存时更新”模式，并手动重新索引客户网格。
exl-id: e4d9d60a-a0d1-4602-924e-a338e56de61d
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# CSV导入后，新客户未显示在客户网格中

本文修复了从`.csv`文件导入后，在&#x200B;**客户** > **所有客户**&#x200B;下看不到新客户的问题。 解决方案是将`customer_grid`索引器设置为“保存时更新”模式，并手动重新索引客户网格。

## 受影响的版本

* Adobe Commerce内部部署2.2.0及更高版本
* Cloud Infrastructure 2.2.0及更高版本上的Adobe Commerce

## 问题

使用本机Adobe Commerce导入功能从`.csv`文件导入新客户后，在手动重新索引`customer_grid`索引器之前，您可能无法在管理员的&#x200B;**客户** > **所有客户**&#x200B;下看到新客户记录。

## 原因

由于性能问题，Adobe Commerce 2.2.0及更高版本中的“按计划更新”索引模式不支持`customer_grid`索引器。

## 解决方案

使用“保存时更新”模式将`customer_grid`索引器配置为重新索引。 为此，请执行以下步骤：

1. 登录到Commerce管理员。
1. 单击&#x200B;**系统** > **工具** > **索引管理**。
1. 选中Customer Grid索引器旁边的复选框。
1. 在&#x200B;**操作**&#x200B;下拉列表中，选择&#x200B;*保存时更新*。
1. 单击&#x200B;**提交**。

我们还建议在配置索引模式后手动重新索引`customer_grid`索引器，以确保索引是最新的并且可以与cron配合使用。 要手动重新索引，请使用以下命令：

`bin/magento indexer:reindex customer_grid`

## 更多信息

链接到我们的开发人员文档中的相关主题：

* [索引概述](https://developer.adobe.com/commerce/php/development/components/indexing/)
* [管理索引器](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers)
