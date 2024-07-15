---
title: “MDVA-15546：列'entity_id' where子句不明确”
description: “MDVA-15546修补程序解决了可能与某些Amazon扩展相关的性能问题。 在中，此问题由异常日志中的以下错误指示： *其中*   *列“entity\\_id”在where子句中模棱两可，查询为：SELECT \\'main\\\_table\\'。\\*， \\'extension\\_attribute\\_amazon\\_order\\_reference\\_id* \\'。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20后，即可使用此修补程序。 修补程序ID为MDVA-15546。”
exl-id: d58c1728-eb7a-49e8-a329-3197f2339b9c
feature: B2B, Commerce Intelligence
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-15546：列“entity_id”，其中子句不明确

MDVA-15546修补程序解决了可能与某些Amazon扩展相关的性能问题。 此问题由异常日志中的以下错误指示： *其中*   *Where子句中的“entity\_id”列不明确，查询为： SELECT \&#39;main\_table\&#39;。\*， \&#39;extension\_attribute\_amazon\_order\_reference\_id* \&#39;。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20时，此修补程序可用。 修补程序ID为MDVA-15546。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.2.5

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce 2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

可能与某些Amazon扩展相关的性能问题。

<u>先决条件</u>：

使用B2B和Amazon\_Payment清理Adobe Commerce。

<u>重现步骤</u>：

1. 转到店面页面。
1. 将产品添加到购物车。
1. 等待或触发cron作业`flush_preview_quotas`。

<u>实际结果</u>：

检查`var/log/exception/log`时，您会看到以下错误：

*`report.ERROR: Cron Jobflush_preview_quotashas an error: SQLSTATE[23000]: Integrity constraint violation: 1052 Column 'entity_id' in where clause is ambiguous, query was: SELECT `main_table`.*, `extension_attribute_amazon_order_reference_id`.`amazon_order_reference_id` AS `extension_attribute_amazon_order_reference_id`, `extension_attribute_amazon_order_reference_id`.`quote_id` AS `extension_attribute_amazon_order_reference_id_quote_id`, `extension_attribute_amazon_order_reference_id`.` sandbox_simulation_reference`, `extension_attribute_amazon_orer{1attribute_amazon_orer_orer_reference` AS `extension_attribute_amazon_amazon_orage_attribute_reference_id{111110 2}extension_attribute_amazon_order_reference_id_confirmed` FROM `quote` AS `main_table` LEFT JOIN `amazon_quote` AS `extension_attribute_amazon_order_reference_id` ON main_table.entity_id = extension_attribute_amazon_order_reference_id.quote_id WHERE ...`*`.`` AS `

<u>预期的结果</u>：

Cron作业完成，且没有错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
