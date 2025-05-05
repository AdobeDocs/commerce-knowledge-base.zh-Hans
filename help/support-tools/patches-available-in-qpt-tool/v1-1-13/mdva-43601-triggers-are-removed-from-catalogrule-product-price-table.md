---
title: 'MDVA-43601：完全重新索引后，从“catalogrule_product_price”表中删除触发器'
description: MDVA-43601修补程序修复了在完全重新索引“catalogrule_rule”或“catalogrule_product”后，从“catalogrule_product_price”表中删除触发器的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43601。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: fdef1e56-79ec-455a-8a29-b82f1c8ceea7
feature: Catalog Management, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-43601：完全重新索引后，从“catalogrule_product_price”表中删除触发器

MDVA-43601修补程序修复了在完全重新索引`catalogrule_rule`或`catalogrule_product`之后从`catalogrule_product_price`表中删除触发器的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-43601。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在对`catalogrule_rule`或`catalogrule_product`进行完全重新索引后，从`catalogrule_product_price`表中删除触发器。

<u>重现步骤</u>：

1. 将所有索引器设置为&#x200B;*按计划*&#x200B;更新。
1. 通过运行以下SQL请求检查为`catalogrule_product_price`表创建的触发器：

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. 通过运行以下命令手动重新索引`catalogrule_rule`或`catalogrule_product`： `bin/magento indexer:reindex catalogrule_rule`
1. 再次检查`catalogrule_product_price`表的触发器。

<u>预期的结果</u>：

完全重新索引后保留`catalogrule_product_price`表中的触发器。

<u>实际结果</u>：

未找到`catalogrule_product_price`表的触发器。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
