---
title: 更新高级报告以在其自己的cron组上运行
description: 本文为Adobe Commerce在Cloud Infrastructure 2.3.0上的已知问题提供了一个修补程序，在该修补程序中，高级报表不显示任何数据。 这是因为高级报告作业“analytics_collect_data”未按计划执行。 本文提供了一个修补程序，该修补程序将创建高级报表核心组“analytics”。
exl-id: 8aff9e2b-d9be-4136-975b-05963e23f55c
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 更新高级报告以在其自己的cron组上运行

本文为Adobe Commerce在Cloud Infrastructure 2.3.0上的已知问题提供了一个修补程序，在该修补程序中，高级报表不显示任何数据。 这是因为未按计划执行高级报告作业`analytics_collect_data`。 本文提供了一个将创建高级报表cron组`analytics`的修补程序。

## 问题

没有数据加载到“高级报告”模块中。

## Patch

该修补程序已附加到本文。 该修补程序将`analytics` cron作业任务从默认组移至`analytics`。

要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[MDVA-19640\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-19640_EE_2.3.0_COMPOSER_v1.patch.zip)

应用修补程序后，请运行以下SQL查询。 必须运行查询才能更改`cron_schedule`表中的记录。

```
UPDATE core_config_data
SET `path` = REPLACE(path, "crontab/default/jobs/analytics", "crontab/analytics/jobs/analytics")
WHERE `path` LIKE "crontab/default/jobs/analytics%";
```

### 兼容的Adobe Commerce版本：

已创建修补程序

* 云基础架构上的Adobe Commerce 2.3.0

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决问题）：2.2.2-2.2.10、2.3.0-2.3.2和2.3.2-p2以及2.3.3，适用于本地Adobe Commerce和云基础架构上的Adobe Commerce

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
