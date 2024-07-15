---
title: 性能缓慢、运行速度缓慢且运行时间较长
description: 本文介绍如何解决因启用了平面表和索引器而导致的站点性能问题以及运行缓慢和卡住cron。
exl-id: a78ca3c3-85b4-40a1-a693-4703dd3ef4b5
feature: Best Practices, Cache, Categories, Catalog Management
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# 性能缓慢、运行速度缓慢且运行时间较长

>[!WARNING]
>
>在任何Adobe Commerce版本上，由于某些扩展仅适用于平面表，因此，如果禁用平面表，则存在风险。 如果您知道有一些扩展使用平面目录索引器，则可能需要在将这些值设置为“*No*”时考虑这一点。

本文介绍如何解决因启用了[平面表和索引器](https://docs.magento.com/m2/ce/user_guide/catalog/catalog-flat.html)而导致的站点性能问题以及运行缓慢和卡住的cron。

受影响的产品和版本

* 云基础架构2.1.x及更高版本上的Adobe Commerce
* Adobe Commerce内部部署2.1.x及更高版本
* Magento Open Source2.1.x及更高版本

## 问题

平面索引器可能导致：

* 严重的SQL负载和站点性能问题。
* 长时间跑步和卡住婴儿车。

## 原因

已启用平面表和索引器。

## 解决方案 {#solution}

从Adobe Commerce和Magento Open Source2.1.x及更高版本开始，使用平面目录不再是最佳实践，因此不建议使用。 据悉，继续使用此功能会导致性能下降和其他索引问题。 要禁用平面目录，请执行以下操作：

1. 在管理员中，导航到&#x200B;**商店** > **设置** > **配置**。
1. 在左侧&#x200B;**目录**&#x200B;下的面板中，选择&#x200B;**目录**。
1. 展开&#x200B;**店面**&#x200B;部分，然后执行以下操作：
   * 将&#x200B;**使用平面目录类别**&#x200B;设置为&#x200B;*否*。
   * 将&#x200B;**使用平面目录产品**&#x200B;设置为&#x200B;*否*。
1. 完成后，单击&#x200B;**保存配置**。 然后在出现提示时，刷新缓存。
1. 通过运行`php bin/magento cache:flush`刷新缓存。

如果由于选项灰显而无法将&#x200B;**使用平面目录类别**&#x200B;和&#x200B;**使用平面目录产品**&#x200B;更改为&#x200B;*否*，请在`app/etc/config.php`中禁用平面索引器：

1. 运行此命令以确保所有索引器都设置为按计划更新： `php bin/magento indexer:set-mode schedule`。
1. 编辑`app/etc/config.php`并找到具有`flat_catalog_product`和`flat_catalog_category`的行 — 将它们从1更改为0以禁用它们。
1. 运行命令`php bin/magento app:config:import`
1. 运行此命令以确认已禁用平面索引器： `php        bin/magento indexer:status`。
1. 通过运行`php bin/magento cache:flush`刷新缓存。

## 相关信息

在我们的支持知识库中，在Cloud](/help/how-to/general/reset-stuck-magento-cron-jobs-manually-on-cloud.md)上手动[重置卡住的Adobe Commerce cron作业。
