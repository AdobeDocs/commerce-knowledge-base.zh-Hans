---
title: Adobe Commerce数据库数值超出范围，“INT”到“BIGINT”
description: 当您无法保存产品更新（如价格更改或删除以及复制产品）时，本文提供了相应的解决方案。
exl-id: e2a00371-9032-4e81-b60e-5456ba35be94
feature: Services
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Adobe Commerce数据库数值超出范围，`INT`到`BIGINT`

>[!WARNING]
>
>在实施本文中的解决方案（`INT`到`BIGINT`架构更新）之前，商家必须始终检查他们将要更改的字段是否与其他表没有任何外键关系。 如果该字段确实与其他表有外键关系，则会出现问题，因为相关字段仍为`INT`。 他们可以使用以下查询来验证这一点。 此查询列出数据库中给定表字段的外键关系：
>
>```mysql
>SELECT 
>     TABLE_NAME,COLUMN_NAME,CONSTRAINT_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME
>FROM
>   INFORMATION_SCHEMA.KEY_COLUMN_USAGE
>WHERE
>     REFERENCED_TABLE_SCHEMA = '<database_name>' AND
>     REFERENCED_TABLE_NAME = '<table_name>' AND
>     REFERENCED_COLUMN_NAME = '<table_field>';
>```

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

当您无法保存产品更新（如价格更改或删除以及复制产品）时，本文提供了相应的解决方案。
您可能会看到错误消息*无法保存库存项目。 请重试。*&#x200B;在产品更新后，您可能无法部署。 在运行`php bin/magento setup:upgrade`时，您还可能会看到以下[!DNL MySQL]错误消息(在云基础架构上的Adobe Commerce上，此错误显示在部署日志中)：

```mysql
SQLSTATE[22003]: Numeric value out of range: 167 Out of range value for column 'value_id' at row 1, query was: INSERT INTO `catalog_product_entity_decimal` (`attribute_id`,`store_id`,`row_id`,`value`) VALUES (?, ?, ?, ?) ON DUPLICATE KEY UPDATE `attribute_id` = VALUES(`attribute_id`), `store_id` = VALUES(`store_id`), `row_id` = VALUES(`row_id`), `value` = VALUES(`value`)
```

本文中介绍的解决方案包括：
* 将`[ AUTO_INCREMENT ]`更新为表中的下一个值或
* `INT`到`BIGINT`架构更新

您使用的解决方案取决于导致问题的原因。 请参阅以下步骤以找出原因。

## 检查原因的步骤


通过在终端中运行以下命令检查主键的最大值： `SELECT MAX(value_id) FROM catalog_product_entity_int;`

如果`max(value_id)`小于`max int(11) [ 4294967296 ]`，且`[ AUTO_INCREMENT ]`的值大于或等于`max int(11) [ 4294967296 ]`，则考虑[将`[ AUTO_INCREMENT ]`更新为表](#update-the-auto-increment-to-the-next-value-from-the-table)中的下一个值。 否则，请考虑[`INT`到`BIGINT`的架构更新](#int_to_bigint_schema_update)。

## 将`AUTO_INCREMENT`更新为表中的下一个值 {#update-the-auto-increment-to-the-next-value-from-the-table}

>[!WARNING]
>
>在更改表之前执行数据库备份。 另外，将站点置于[维护模式](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#maintenance-mode)。 此外，还建议在进行更改后对数据库表（仅对进行了更改的表）运行[!DNL MySQL]优化命令。

>[!NOTE]
>
>对特定表运行优化命令时，站点应处于维护模式。 这将完全重建表，并在从表删除数据后释放空间。

如果显示的值小于`max int(11) [ 4294967296 ]`（如下例终端输出所示），则表`[ AUTO_INCREMENT ]`已更改为大于或等于`max [ int(11) ]`值的数字。

```mariadb
MariaDB [xxx]> SELECT MAX(value_id) FROM catalog_product_entity_int;
+---------------------+
| MAX(source_item_id) |
+---------------------+
|          4283174130 |
+---------------------+
```

要检查是否已发生这种情况，请在终端中运行以下命令：

```
MariaDB [xxx]> show create table catalog_product_entity_int;

...
) ENGINE=InnoDB AUTO_INCREMENT=4294967297 DEFAULT CHARSET=utf8 COMMENT='Catalog Product Integer Attribute Backend Table';
```

如上面的示例输出所示，表`[ AUTO_INCREMENT ]`已更改为大于`max int(11) [ 4294967296 ]`的数字。 解决方案是将`[ AUTO_INCREMENT]`更新为表中的下一个值：

```
ALTER TABLE catalog_product_entity_int AUTO_INCREMENT = 4283174131;
```

## `INT`到`BIGINT`架构更新 {#int_to_bigint_schema_update}

但是，在运行以下查询`SELECT MAX(value_id) FROM catalog_product_entity_int;`时，如果显示的值大于`max int(11) [ 4294967296 ]`，请考虑执行`INT`到`BIGINT`的架构更新。 数据类型`BIGINT`的值范围更大。

为此，请执行以下操作：

1. 在&#x200B;*app/code/*&#x200B;目录中创建一个自定义模块。
1. 在自定义模块中创建&#x200B;*db_schema.xml*。 在&#x200B;*db_schema.xml*&#x200B;中，您将数据类型设置为`BIGINT`。
1. 添加以下内容，然后执行`bin/magento setup:upgrade`以将上述更改应用到相应的表。

```
<?xml version="1.0"?>
<schema xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Setup/Declaration/Schema/etc/schema.xsd">
    <table name="catalog_product_entity_int">
        <column xsi:type="bigint" name="value_id" unsigned="false" nullable="false" identity="true"
                comment="Value ID"/>
    </table>
</schema>
```


## 相关阅读

* Commerce安装指南中的[常规 [!DNL MySQL] 指南](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/database-server/mysql.html)
* [数据库上载已断开与 [!DNL MySQL]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/database-upload-loses-connection-to-mysql.html)的连接（在我们的支持知识库中）
* 我们的支持知识库中的[云基础架构上Adobe Commerce的数据库最佳实践](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/database-best-practices-for-magento-commerce-cloud.html)
* 在我们支持知识库中，[Adobe Commerce中关于云基础架构的最常见数据库问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/best-practices/database/most-common-database-issues-in-magento-commerce-cloud.html)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
