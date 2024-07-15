---
title: 'MDVA-32655：“quoteItemCleaner”使用者每次执行时执行一条消息'
description: MDVA-32655修补程序在删除多个产品后，将使用者“quoteItemCleaner”的“进行中”消息状态修复为正确的“完成”消息。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18后，即可使用此修补程序。 修补程序ID为32655。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: 07213430-f779-4a53-89fd-bc3905e13675
feature: Quotes
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32655：“quoteItemCleaner”使用者每次执行时执行一条消息

MDVA-32655修补程序在删除多个产品后，将消费者`quoteItemCleaner`的不正确的“进行中”消息状态修复为正确的“完成”消息。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18时，此修补程序可用。 修补程序ID为32655。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.3

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`quoteItemCleaner`使用者每次执行时只执行一条消息。

<u>重现步骤</u>：

1. 检查`queue_message_status`数据库表并确保所有现有队列消息都处于“完成”状态（状态ID 4）。
1. 停止自动Adobe Commerce cron执行。
1. 创建两个或三个简单的产品。
1. 对这三个简单的产品执行批量删除。
1. 在`queue_message_status`表中，您看到`catalog_product_removed_queue`主题有三个新记录，其状态ID为2 （新记录）。
1. 运行以下命令以处理这些挂起`catalog_product_removed_queue`的消息：

   ```bash
   bin/magento queue:consumers:start quoteItemCleaner --single-thread --max-messages=100
   ```

<u>预期的结果</u>：

```sql
select * from queue_message_status s join queue q on s.queue_id = q.id where q.name = "catalog_product_removed_queue";
```

所有`catalog_product_removed_queue`消息状态都已更新为完成(ID=4)。

<u>实际结果</u>：

只有三个记录中的一个记录更新为“完成”状态(ID = 4)。 另外两条消息的状态为status ID = 3 （进行中）。 生成具有未处理队列消息的积压。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
