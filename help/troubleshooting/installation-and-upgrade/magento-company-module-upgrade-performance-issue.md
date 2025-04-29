---
title: B2B 1.5.2更新后Magento_Company模块升级中的性能问题
description: 本文为B2B 1.5.2更新后Magento_Company模块升级中的性能问题提供了修补程序，解决了对company_structure表中大型数据集的处理时间过长的问题。
feature: B2B, Upgrade
role: Admin, Developer
source-git-commit: d06f0045b4c4c1615bd3abec963eb17fdee93860
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# B2B 1.5.2更新后Magento_Company模块升级中的性能问题

本文为B2B 1.5.2更新后`Magento_Company`模块升级中的性能问题提供了一个修补程序，用于解决`company_structure`表中大型数据集（约100,000多条记录）的处理时间过长的问题。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.4.6-px + B2B 1.5.2
* Adobe Commerce（所有部署方法） 2.4.7-px + B2B 1.5.2
* Adobe Commerce（所有部署方法）2.4.8 + B2B 1.5.2

## 问题

在更新到B2B 1.5.2之后升级`Magento_Company`模块时，处理`company_structure`表中的大量记录(~100,000+)会花费非常长的时间。

<u>先决条件</u>：

* 应安装ACSD-65540_B2B_1.5.2.patch。
* Adobe Commerce 2.4.6 - 2.4.8
* 应用ACSD-65540修补程序的B2B 1.5.0、1.5.1或B2B 1.5.2

<u>重现步骤</u>：

1. 将公司分配给母公司以建立公司层次结构。 有关详细信息，请参阅Adobe Commerce B2B指南中的[管理公司层次结构](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/company-management/manage-company-hierarchy)。
1. 将B2B升级到1.5.2版本。

<u>预期的结果</u>：

升级成功完成。

<u>实际结果</u>：

如果`company_structure`表中有许多记录，则升级`Magento_Company`模块需要很长时间才能完成。

## 解决方案

要解决此问题，请执行以下步骤：

1. 将B2B模块更新至1.5.2版本：

   ```
   composer require magento/module-b2b:1.5.2 --no-update
   composer update magento/module-b2b
   ```

1. 应用[ACSD-65540_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2.zip)。

1. 应用附加的[ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch](/help/troubleshooting/installation-and-upgrade/assets/ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch.zip)。
1. 在应用修补程序后运行`bin/magento setup:upgrade`。

### 如何应用修补程序

解压缩文件，并在我们的支持知识库中参阅[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)获取相关说明。

### 使用云修补程序应用修补程序

对于Adobe Commerce on Cloud商家，请按照以下步骤操作：

1. 将cloud-patches模块的版本更新为1.1.5，以安装作为MCLOUD-13605分发的ACSD-65540_B2B_1.5.2.patch。

   >[!NOTE]
   >
   >要检查是否已安装修补程序，请运行：
   > `./vendor/bin/magento-patches -n status | grep MCLOUD-13605`

   ```
   composer require magento/magento-cloud-patches:1.1.5 --no-update
   composer update magento/magento-cloud-patches
   ```

1. 将ACSD-65540_B2B_1.5.2_DEPENDENT_ACSD-65684_B2B_1.5.2.patch添加到`m2-hotfixes`目录。
1. 提交并推送更改以启动重新部署和`bin/magento setup:upgrade`。 有关说明，请参阅我们的Adobe Commerce on Cloud指南中的[应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

* [由于缺少REGEXP_LIKE函数](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/sql-syntax-error-due-to-missing-regexp-like-function)，升级到B2B 1.5.2失败，出现SQL语法错误
