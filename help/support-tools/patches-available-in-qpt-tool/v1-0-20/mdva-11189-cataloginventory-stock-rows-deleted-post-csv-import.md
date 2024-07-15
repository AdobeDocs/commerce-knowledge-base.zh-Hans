---
title: 'MDVA-11189：CSV导入后删除了cataloginventory_stock行'
description: 11189于MDVA的Adobe Commerce修补程序修复了在导入.csv文件以更新产品库存后，删除“cataloginventory_stock”表中的行时出现的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20后，即可使用此修补程序。 修补程序ID为MDVA-1189。 请注意，Adobe Commerce 2.3.5中已修复此问题。
exl-id: 84e1979c-826c-4c01-b0c7-8054bb4b23f0
feature: Catalog Management, Data Import/Export, Inventory, Orders
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-11189：CSV导入后删除了cataloginventory_stock行

11189于MDVA的Adobe Commerce修补程序修复了在导入.csv文件以更新产品库存后，`cataloginventory_stock`表中的行被删除的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20时，此修补程序可用。 修补程序ID为MDVA-1189。 请注意，Adobe Commerce 2.3.5中已修复此问题。

## 受影响的产品和版本

**在Cloud Infrastructure 2.2.3上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce（所有部署方法） 2.3.0-2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了在导入`.csv`以更新产品库存后，`cataloginventory_stock`表中的行被删除的问题。

<u>要再现的步骤：</u>

1. 在数据库中运行以下MySQL命令： `select count(*) from cataloginventory_stock_status;`
1. 记下行数。
1. 按如下方式设置crontab： `* * * * * /usr/bin/php <path to installation>/bin/magento cron:run  | grep -v "Ran jobs by schedule" >> <path to installation>/var/log/cron.log 2>&1`
1. 转到&#x200B;**系统** > **工具** > **索引管理**&#x200B;中的“管理”面板。
1. 将索引器设置为&#x200B;*按计划更新。*
1. 转到&#x200B;**系统** > *数据传输* > **导出**。
1. 将&#x200B;**实体类型**&#x200B;设置为等于&#x200B;*产品* > **继续**。
1. 打开保存的`.csv`文件>“移除除SKU和QTY之外的所有列”。
1. 将所有产品的数量更新为150。
1. 保存`.csv`文件。
1. 转到&#x200B;**系统** > *数据传输* > **导入** 。
1. 设置以下值：
   1. 实体类型：*产品*
   1. 导入行为： *添加/更新*
   1. 将所有其他值保留为默认值。
   1. 选择“文件”以选择目录产品电子表格。
1. 单击&#x200B;**检查数据** > **导入**。 等待5-10分钟通过。
1. 在数据库中，运行以下MySQL命令：
   `select count(*) from cataloginventory_stock_status;`

<u>实际结果：</u>

导入CSV以更新库存后，`cataloginventory_stock`中的行数会减少。

<u>预期结果：</u>

CSV导入后，`cataloginventory_stock`中的行数应保持不变，以更新库存。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
