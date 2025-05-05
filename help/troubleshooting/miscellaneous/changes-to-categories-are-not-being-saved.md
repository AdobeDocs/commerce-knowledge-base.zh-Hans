---
title: 未保存对类别所做的更改
description: 本文修复了在通过Commerce管理员更新产品类别时，更改不会显示在管理员和店面中的问题。 问题是由于“catalog_category_entity”表中的数据损坏导致的。 要解决此问题，请修复或删除表中有问题的类别更新记录。 之后，您应该能够使用管理员更新产品类别。
exl-id: d951205c-add9-478c-9c7d-2ba975d53b14
feature: Categories
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---

# 未保存对类别所做的更改

本文修复了在通过Commerce管理员更新产品类别时，更改不会显示在管理员和店面中的问题。 问题是由于`catalog_category_entity`表中的数据损坏导致的。 要解决此问题，请修复或删除表中有问题的类别更新记录。 之后，您应该能够使用管理员更新产品类别。

## 问题

在管理员中对产品类别进行更改并保存后，新的更新既不会保存，也不会显示在管理员和店面中。

### 重现问题的步骤

1. 转到&#x200B;**目录** > **类别**。
1. 选择类别。
1. 进行更改，然后单击&#x200B;**保存**。
1. 显示消息： *您已保存类别*。
1. 请注意，您所做的更改尚未保存。

## 可能的原因： `catalog_category_entity`表中的数据已损坏

问题是由数据库(DB)中受影响的类别记录的`created_in`列中的相同值引起的。

![catalog_category_entity表中的数据已损坏](assets/catalog_category_entity.png)

详细信息：

* `catalog_category_entity`数据库表有两个或多个受影响类别的记录（这些记录具有相同的`entity_id`值）。
* 这些类别记录在`created_in`列&#x200B;**中有**&#x200B;个相同的值。

### 对于同一类别，第二个数据库条目（以及所有后续条目）如何显示在数据库中？

受影响类别的第二个DB记录（可能还有后续记录）表示已使用Magento\_Staging模块计划了类别更新。 模块为`catalog_category_entity`中的类别创建附加记录，这是预期的应用程序行为；问题是这些记录的`created_in`列具有相同的值。

### 如何显示相同的值？

我们无法确切地说明数据损坏的原因。 可能的原因包括：

* 自定义项（代码、主题等）
* 数据迁移不正确
* 从备份还原的数据不正确

据我们所知，此类数据损坏不适用于“干净”（现成）Adobe Commerce实例，并且无法在没有自定义设置的Adobe Commerce安装中重现。

### 如何验证这是您的问题

对于受影响的类别，`catalog_category_entity`表应有多个记录（记录应具有相同的`entity_id`值），并且其中至少有两个记录应具有相同的`created_in`值。 这样，暂存计划更新将不会显示在Commerce管理员中；您只会看到空的“计划更改”块。

#### 验证步骤

1. 访问数据库中的catalog\_category\_entity表。
1. 按entity\_id筛选实体，其中entity\_id标识受影响的类别。
1. 如果created\_in列中的值对于具有相同entity\_id的不同条目是相同的，则就是这样。 通常情况下，每个记录的`created_in`值都不相同。

![catalog_category_entity表中的数据已损坏](assets/catalog_category_entity.png)

## 解决方案

您可以选择以下解决方案之一：

1. **删除**&#x200B;有问题的类别更新记录
1. **修复**&#x200B;有问题的类别更新记录

### 删除有问题的类别更新记录

在此解决方案中，您需要为初始类别记录设置正确的`updated_in`值，并删除此类别的所有其他记录。 这将删除所有计划的类别更新。

请按照以下步骤操作：

1. 查找具有受影响类别的`entity_id`的数据库记录。
1. 选择`updated_in`列中整数最大的记录。
1. 从所选记录中复制`updated_in`值。
1. 选择具有`row_id` = `entity_id` （初始类别记录）的记录，并将复制的值粘贴到此记录的`updated_in`列。
1. 删除`row_id`不等于`entity_id`的行。

### 修复有问题的类别更新记录

1. 查找具有相同`entity_id`和相同`created_in`值的类别记录。
1. 选择`row_id` = `entity_id`的记录并复制`updated_in`值。
1. 选择`row_id`不等于`entity_id`的记录，并将复制的`updated_in`值粘贴为`created_in`值。 请参见下面的屏幕快照作为插图。    ![正在复制created_in值.png](assets/copy_created-in_value.png)
1. 验证`staging_update`表中是否存在类别更新记录，即（步骤3中的）已更新的`created_in`值。 *例如：*&#x200B;如果复制的`created_in`值为1509281953，则`staging_update`表中必须存在具有`row_id` = 1509281953的实体。

## 相关阅读

[在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
