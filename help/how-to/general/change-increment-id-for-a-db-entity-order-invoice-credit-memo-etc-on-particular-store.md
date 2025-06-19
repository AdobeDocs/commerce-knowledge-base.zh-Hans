---
title: 更改特定商店中数据库实体（订单、发票、贷项通知单等）的增量ID
description: 本文讨论如何使用“ALTER TABLE”SQL语句更改特定Adobe Commerce存储上Adobe Commerce数据库(DB)实体（订单、发票、贷项通知单等）的增量ID。
exl-id: 3704dd97-3639-44dc-9b8b-cf09f0c04e6c
feature: Invoices
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# 更改特定商店中数据库实体（订单、发票、贷项通知单等）的增量ID

本文讨论如何使用`ALTER TABLE` SQL语句更改特定Adobe Commerce存储中Adobe Commerce数据库(DB)实体（订单、发票、贷项通知单等）的增量ID。

## 受影响的版本

* Adobe Commerce内部部署：2.x.x
* 云基础架构上的Adobe Commerce：2.x.x
* MySQL：任何[支持的版本](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)

## 您何时需要更改增量ID（案例）

在以下情况下，您可能需要更改新数据库实体的增量ID：

* 在Live站点上进行硬备份还原之后
* 某些订单记录已丢失，但支付网关（如PayPal）已使用其ID作为您的当前商家帐户。 在这种情况下，付款网关将停止处理具有相同ID的新订单，并返回“重复发票ID”错误

>[!NOTE]
>
>您还可以通过在PayPal的“付款接收首选项”中允许每个发票ID多次付款，修复PayPal的付款网关问题。 请参阅我们的支持知识库中的[PayPal网关被拒绝的请求 — 重复发票问题](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26838)。

## 必备步骤

1. 查找应更改新增量ID的存储和实体。
1. [连接](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote)到您的MySQL数据库。 对于云基础架构上的Adobe Commerce，您首先需要[SSH连接到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)。
1. 使用以下查询检查实体序列表的当前auto\_increment值：

```sql
SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
```

### 示例

如果您在&#x200B;*ID=1*&#x200B;的存储区中检查订单的自动递增，则表名将是：

```sql
'sequence_order_1'
```

如果`auto_increment`列的值为&#x200B;*1234*，则在&#x200B;*ID=1*&#x200B;的商店下个订单将具有&#x200B;*ID \#100001234*。

### 相关文档

* [在我们的开发人员文档中设置远程MySQL数据库连接](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql-remote)。

## 更新实体以更改增量ID

使用以下查询更新实体：

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!WARNING]
>
>重要信息：新增量值必须大于当前增量值，不得小于！

### 示例

执行以下查询后：

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

下一个在&#x200B;*ID=1*&#x200B;商店下单的订单将具有&#x200B;*ID \#100002000*。

## 有关生产环境(Cloud)的其他建议步骤

在云基础架构上的Adobe Commerce的生产环境中执行`ALTER TABLE`查询之前，我们强烈建议执行以下步骤：

* 测试在暂存环境中更改增量ID的整个过程
* [创建](/help/how-to/general/create-database-dump-on-cloud.md)数据库备份，以便在出现故障时还原您的生产数据库

## 相关文档

* 在我们的支持知识库中[在云上创建数据库转储](/help/how-to/general/create-database-dump-on-cloud.md)
* 在开发人员文档中[SSH到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
