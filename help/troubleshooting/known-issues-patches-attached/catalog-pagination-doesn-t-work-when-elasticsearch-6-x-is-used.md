---
title: 目录分页不适用于Elasticsearch6.x
description: 本文为Adobe Commerce问题提供了一个修补程序，该问题导致目录分页在Elasticsearch6.x上不起作用。
exl-id: 60a423de-cf3a-4d73-a7cf-b6d9e95042ca
feature: Catalog Management, Categories, Search, Services
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 目录分页不适用于Elasticsearch6.x

本文为Adobe Commerce问题提供了一个修补程序，该问题导致目录分页在Elasticsearch6.x上不起作用。

以下修补程序解决了在将Elasticsearch6.x用作目录搜索引擎的部署中Adobe Commerce 2.3.3用户遇到的问题。 用户尝试导航超过搜索结果的首页时看到错误消息。

安装此修补程序后，用户将能够翻阅所有搜索结果。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.3
* Adobe Commerce内部部署2.3.3
* Magento Open Source2.3.3
* Elasticsearch6.x

## 问题

在Magento Open Source、Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure中发现了一个问题，即如果切换页面，则搜索结果页面分页不起作用。

<u>重现步骤</u>：

1. 安装Adobe Commerce。
1. 将Elasticseach 6启用为目录搜索引擎。
1. 向类别中添加许多超过管理员中设置的1页限制的产品。 **注意**： 12是Adobe Commerce 2.3.3中每页显示的默认产品数。
1. 在店面中打开类别（搜索结果或类别页面），然后转到第2页。

<u>预期的结果</u>：

产品应显示在第二页上。

<u>实际结果</u>：

**“***找不到与所选内容匹配的产品***”**&#x200B;消息显示在第二页上。

## 解决方案

要解决此问题，请应用本文附带的修补程序。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[在Elasticsearch6.x修补程序上下载目录分页问题](assets/Catalog_pagination_issue_on_Elasticsearch_6_composer-2019-10-11-08-07-41.patch.zip) — 该修补程序与所有受影响的版本和版本兼容。

>[!WARNING]
>
>Adobe强烈建议尽快应用修补程序，即使您还没有出现任何症状。

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
