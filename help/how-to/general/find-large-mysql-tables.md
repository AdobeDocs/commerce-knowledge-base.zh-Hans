---
title: 查找大型MySQL表
description: '''要识别大型表，请按照[连接到数据库](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database)文章中的说明连接到数据库，然后运行以下命令，其中''project_id''是您的Cloud项目ID：'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# 查找大型MySQL表

要识别大型表，请按照[连接到数据库](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database)文章中所述连接到数据库，然后运行以下命令，其中`project_id`是您的Cloud项目ID：

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

这将显示表的完整列表及其大小。 您可以浏览列表，并找出哪些表由于规模较大而需要注意。
