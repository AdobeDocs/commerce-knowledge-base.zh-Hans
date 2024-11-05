---
title: 查找大型MySQL表
description: '''要识别大型表，请按照[连接到数据库](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database)文章中的说明连接到数据库，然后运行以下命令，其中''project_id''是您的Cloud项目ID：'''
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '111'
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

## 相关阅读

[在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
