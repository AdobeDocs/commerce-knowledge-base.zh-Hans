---
title: 存储前端目录页面时出现503错误，日志中显示“完整性约束冲突”
description: 本文为云基础架构2.2.0中已知的Adobe Commerce提供了修补程序，该问题与无法访问存储前端目录页面相关。
exl-id: ad363744-756a-48b9-ae11-58642e0ca6a4
feature: Catalog Management, Logs
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# 存储前端目录页面时出现503错误，日志中显示“完整性约束冲突”

>[!NOTE]
>
>本文提供了修补程序作为解决方法，但该问题已在Adobe Commerce on cloud infrastructure v2.3.3版本中永久修复，建议您升级到v2.3.3。按照开发人员文档中的[升级Adobe Commerce版本](https://devdocs.magento.com/cloud/project/project-upgrade.html)中的步骤操作。

本文为云基础架构2.2.0上与存储前端目录页相关的已知Adobe Commerce问题提供了一个修补程序，该问题在日志中带有类似于以下内容的错误消息： *完整性约束违规： 1062键“PRIMARY”的重复条目“%entry%”，查询为： INSERT INTO \&#39;search\_tmp\_%number%*。

## 问题

存储前端目录页面意外变为不可访问。 错误日志具有类似于以下内容的错误描述： *完整性约束冲突： 1062键“PRIMARY”的重复条目“%entry%”，查询为： INSERT INTO \&#39;search\_tmp\_%number%*。

该问题与搜索有关，并且是由于重新索引后存在过时索引以及新索引造成的。

## 解决方案

要解决此问题，需要从Elasticsearch中删除过时的索引，并应用修补程序以防止这些索引出现。

要列出所有索引，请使用以下命令：

<pre>curl -XGET%elasticsearch_domain%：%elasticsearch_port%/_cat/indices</pre>

要删除过时的索引，请在数据库中查找这些索引，然后使用以下命令：

```bash
curl -X DELETE %elasticsearch_domain%:%elasticsearch_port%/%product_id%_v%outdated_version%
```

示例：

```bash
curl -X DELETE 127.0.0.1:9200/magento2_product_8_v332
```

## Patch

修补程序已附加到本文。 要下载补丁程序，请向下滚动到文章末尾，然后单击所需的文件名，或单击以下链接之一：

[下载MDVA-9590\_EE\_2.2.0\_COMPOSER\_v2.patch](assets/MDVA-9590_EE_2.2.0_COMPOSER_v2.patch.zip)

[下载MDVA-13203\_EE\_2.2.4\_V1\_COMPOSER.patch](assets/MDVA-13203_EE_2.2.4_V1_COMPOSER.patch.zip)

## 兼容的Adobe Commerce版本

为以下版本和版本创建了修补程序：

* 云基础架构2.2.0 (`MDVA-9590_EE_2.2.0_COMPOSER_v2.patch`)上的Adobe Commerce
* 云基础架构2.2.4 (`MDVA-13203_EE_2.2.4_V1_COMPOSER.patch`)上的Adobe Commerce

`MDVA-9590_EE_2.2.0_COMPOSER_v2`修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3
* Adobe Commerce内部部署2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3

`MDVA-13203_EE_2.2.4_V1_COMPOSER`修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3
* Adobe Commerce内部部署2.0.X、2.1.X、2.2.X和2.3.0 - 2.3.3

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 有用的链接

* 在我们的支持知识库中，[Adobe Commerce在云基础架构上的日志文件位置入门计划架构](/help/how-to/general/log-locations-directories-for-starter-plan.md)。
* 在我们的支持知识库中，[Adobe Commerce在云基础架构上的日志文件位置Pro规划体系结构](/help/how-to/general/log-locations-directories-for-pro-plan-integration-staging-production.md)。
* 在开发人员文档中，为Adobe Commerce](https://devdocs.magento.com/guides/v2.3/cloud/trouble/environments-logs.html)添加[日志文件位置。

## 附加文件
