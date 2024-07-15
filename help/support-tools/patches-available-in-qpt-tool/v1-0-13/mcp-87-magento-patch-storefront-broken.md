---
title: 'MCP-87 Adobe Commerce补丁：店面已损坏'
description: MCP-87 Adobe Commerce修补程序修复了目录的库存重新索引速度缓慢的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。
exl-id: 048b2764-6bbf-4a02-9a0a-dbea4e48f92a
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# MCP-87 Adobe Commerce修补程序：店面已损坏

MCP-87 Adobe Commerce修补程序修复了目录的库存重新索引速度缓慢的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构2.4.0上的Adobe Commerce 。

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.1 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

大配置文件目录的股票重新指数非常慢。

<u>要再现的步骤：</u>

1. 登录到“管理面板”。
1. 导航到&#x200B;**产品** > **目录**。
1. 选择“产品”网格中的所有项目。
1. 在“选择产品操作”下拉列表中选择&#x200B;**更新属性**。 单击&#x200B;**提交**。
1. 从“高级设置”选项卡单击&#x200B;**高级清单**。 将&#x200B;**库存可用性**&#x200B;更改为&#x200B;*库存*。 单击&#x200B;**保存**。
1. 手动执行完全重新索引，从根目录执行以下命令： `bin/magento indexer:reindex`

<u>预期结果：</u>

股票索引器会快速重新编制指数。

<u>实际结果：</u>

Stock索引器运行速度非常慢和/或没有完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
