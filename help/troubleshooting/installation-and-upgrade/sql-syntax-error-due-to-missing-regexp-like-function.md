---
title: 由于缺少REGEXP_LIKE函数，升级到B2B 1.5.2失败，并出现SQL语法错误
description: 针对在尝试更新company_structure表时由于缺少REGEXP_LIKE函数而发生SQL语法错误的问题，本文提供了一个修补程序。
feature: B2B, Upgrade
role: Admin, Developer
exl-id: c5fe316c-99e3-482e-80b5-25aaae371230
source-git-commit: f83b82a95d4592252c8923720e90733115c52d87
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# 由于缺少REGEXP_LIKE函数，升级到B2B 1.5.2失败，并出现SQL语法错误

本文为尝试更新`company_structure`表时由于缺少`REGEXP_LIKE`函数而发生的SQL语法错误提供了修补程序。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.4.6-px + B2B 1.5.2（使用[!DNL MariaDB] 10.6）
* Adobe Commerce（所有部署方法） 2.4.7-px + B2B 1.5.2（使用[!DNL MariaDB] 10.6）

## 问题

由于尝试更新`company_structure`表时缺少`REGEXP_LIKE`函数，升级到B2B版本1.5.2失败，并出现SQL语法错误。

<u>先决条件</u>：

* MariaDB 10.6
* Adobe Commerce 2.4.6x或2.4.7x
* B2B版本1.5.0或1.5.1

<u>重现步骤</u>：

1. 将公司分配给母公司以建立公司层次结构。 有关详细信息，请参阅Adobe Commerce B2B指南中的[管理公司层次结构](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy)。
1. 将B2B升级到1.5.2版本。

<u>预期的结果</u>：

升级成功完成。

<u>实际结果</u>：

`bin/magento setup:upgrade`失败，出现以下错误：

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^123(/.+)?$'))
```

## 解决方案

要解决此问题，请执行以下步骤：

1. 将B2B模块更新至1.5.2版本：

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. 应用附加的[ACSD-65540_B2B_1.5.2.zip](assets/ACSD-65540_B2B_1.5.2.zip)修补程序。 有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
1. 运行`bin/magento setup:upgrade`。

### 使用云修补程序应用修补程序

对于云基础架构上的Adobe Commerce，请执行以下步骤：

1. 将`cloud-patches`模块的版本更新为1.1.5：

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. 提交并推送更改以启动重新部署。 有关说明，请参阅我们的Adobe Commerce on Cloud指南中的[应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。
