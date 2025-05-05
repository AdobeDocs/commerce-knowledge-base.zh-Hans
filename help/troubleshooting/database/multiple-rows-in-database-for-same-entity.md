---
title: 同一实体在数据库中有多行
description: 本文为数据库中的同一实体ID存在多行问题提供了解决方案。
feature: Catalog Management, Categories, Services, Storefront
role: Developer
exl-id: 09d5c321-9c45-4041-b6f6-831efca0977e
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# 同一实体的数据库中的多行

本文为数据库中的同一实体ID存在多行问题提供了解决方案。

## 受影响的产品和版本：

* Adobe Commerce（所有版本）

## 问题

数据库中同一实体ID有多个行。

例如，在运行此查询时收到具有重复实体ID的记录列表后：

```
SELECT * FROM $entityTable WHERE $column = <$entityID> ORDER BY created_in;
```

其中`$entityID = ID`个类别/产品/购物车价格规则/目录价格规则/CMS页面。

| 实体 | $entityTable | $column |
|------------------|-----------------------------------|------------------|
| 类别/产品 | catalog_category_entity/catalog_product_entity | entity_id |
| 购物车价格规则/目录价格规则 | salesrule/catalogrule | rule_id |
| CMS页面 | cms_page | page_id |

## 原因

这是预期行为。 多行由内容暂存功能创建：

* 如果指定的开始日期没有结束日期，则至少有两行具有相同的实体/规则/页面ID。 一行表示实体的原始状态（`created_in=1`所在的行），一行表示计划更新的&#x200B;*结束*。

* 如果指定了带有结束日期的开始日期，则至少会有三行具有相同的实体/规则/页面ID。 一行表示实体的原始状态（`created_in=1`所在的行），一行表示计划更新的&#x200B;*开始*，一行表示计划更新的&#x200B;*结束*。

例如，在此查询中：

```
SELECT row_id, entity_id, created_in, updated_in FROM catalog_product_entity WHERE entity_id = 483 ORDER BY created_in;
```

![multiple_rows_in_database.png](assets/multiple_rows_in_database.png)

* `created_in`和`updated_in`值应遵循以下模式：当前行的`created_in`值等于上一行的`updated_in`值。 此外，第一行应包含`created_in = 1`，最后一行应包含`updated_in = 2147483647`。 （如果只有一行，则必须看到`created_in=1`和`updated_in=2147483647`）。

### 为什么第二个数据库条目（以及所有后续条目）会出现在同一实体的数据库中？

* 受影响实体的第二条DB记录（可能还有下一条）表示已使用`Magento_Staging`模块计划了内容暂存更新，这将为相应表中的实体生成额外记录。

仅当记录的`created_in`或`updated_in`列具有相同的值时，才会出现问题。

## 解决方案

这是预期行为，仅当行之间存在差异时，才会导致出现问题。

## 相关阅读

* [对类别的更改未保存在我们的支持知识库中](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/changes-to-categories-are-not-being-saved.html?lang=zh-Hans)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
