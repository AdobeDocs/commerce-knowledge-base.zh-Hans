---
title: 'ACSD-58739：部分重新索引引发错误'
description: 应用ACSD-55241修补程序以修复部分重新索引引发错误的Adobe Commerce问题。
feature: Inventory, Products
role: Admin, Developer
source-git-commit: b21eab3bf8ec492f0b1c5be9c13c6c579f43fe44
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-58739：部分重新索引引发错误

ACSD-58739修补程序修复了部分重新索引引发错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-58739。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

部分重新索引引发错误。

<u>重现步骤</u>：

1. 将从属连接设置添加到`app/etc/ev.php`。
1. 生成最多10000个产品并执行以下命令：

   ```
   bin/magento index:reindex
   ```

1. 将生成的产品ID添加到`catalogsearch_fulltext_cl`数据库表中。

   ```
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. 执行以下命令可触发部分重新索引：

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. 检查`var/log/support_report.log`文件。

<u>预期的结果</u>

没有错误。

<u>实际结果</u>：

*未找到基表或视图*&#x200B;执行部分重新索引时出现错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。