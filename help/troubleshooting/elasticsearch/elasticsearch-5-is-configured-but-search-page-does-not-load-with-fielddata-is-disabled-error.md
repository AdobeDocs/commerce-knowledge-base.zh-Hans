---
title: 已配置Elasticsearch5，但搜索页面未加载，并出现“Fielddata已禁用……”错误
description: '本主题介绍如何修复Elasticsearch5的问题，该页面不加载搜索页面，并且会引发与以下内容类似的异常：'
exl-id: f5fa8144-4e7c-45ce-89d0-a8367e91d6db
feature: Cache
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 已配置Elasticsearch5，但搜索页面未加载，并出现“Fielddata已禁用……”错误

本主题介绍如何修复Elasticsearch5的问题，该页面不加载搜索页面，并且会引发与以下内容类似的异常：

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## 受影响的版本

* Adobe Commerce 2.2.x
* Elasticsearchv.5

>[!NOTE]
>
>Adobe Commerce 2.3.x已弃用Elasticsearchv.5

## 问题

前提条件：配置了Elasticsearch5。

在搜索请求中，日志中会生成以下异常：

```bash
{"0":"{\"error\":{\"root_cause\":[{\"type\":\"illegal_argument_exception\",\"reason\":\"Fielddata is disabled on text fields by default. Set fielddata=true on [%attribute_code%]] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory.\"}].
```

## 原因

默认情况下，分层导航中只能使用某些类型的产品属性。 它们是“是/否”、“下拉列表”、“多重选择”和“价格”。 这就是为什么在Commerce管理中，不能将任何其他类型的属性设置为&#x200B;**用于分层导航** = *可筛选*&#x200B;或&#x200B;**用于搜索结果的分层导航** = *是*。 但是，通过直接更改数据库中的`is_filterable`和`is_filterable_in_search`值，在技术上有可能绕过此限制。 如果发生这种情况，并且任何其他属性类型（如日期、文本等）设置为在分层导航中使用，则Elasticsearch5会引发异常。

要确保出现这种情况，您需要确定是否存在除Dropdown、Multipleselect和Price之外的、设置为在分层导航中使用的任何其他属性。 运行以下查询以搜索这些属性：

```sql
SELECT ea.attribute_code, ea.frontend_input, cea.is_filterable, cea.is_filterable_in_search FROM eav_attribute AS ea
    -> INNER JOIN catalog_eav_attribute AS cea ON ea.attribute_id = cea.`attribute_id`
    -> WHERE (is_filterable = 1 OR is_filterable_in_search = 1) AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
```

结果将包含用于分层导航的属性列表，该属性的类型不允许此操作。 请执行下节中所述的步骤以修复此问题。

## 解决方案

要解决此问题，您需要将`is_filterable`（即用于分层导航）和`filterable_in_search`（即用于搜索结果分层导航）设置为“0”（不使用）。 为此，请执行以下步骤：

1. 创建数据库备份。
1. 使用数据库工具（如[phpMyAdmin](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/optional-software#phpmyadmin)），或者从命令行手动访问数据库以运行以下SQL查询：

   ```sql
   UPDATE catalog_eav_attribute AS cea
       INNER JOIN eav_attribute AS ea
           ON ea.attribute_id = cea.attribute_id
   SET cea.is_filterable = 0, cea.is_filterable_in_search = 0
   WHERE (cea.is_filterable = 1 OR cea.is_filterable_in_search = 1)
       AND frontend_input NOT IN ('boolean', 'multiselect', 'select', 'price');
   ```

1. 使用以下命令运行“目录搜索”完整重新索引：

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 通过运行清理缓存

   ```bash
   bin/magento cache:clean
   ```

或在Commerce管理员中的&#x200B;**系统** > **工具** > **缓存管理**&#x200B;下。

现在，您应该能够毫无问题地执行目录搜索。
