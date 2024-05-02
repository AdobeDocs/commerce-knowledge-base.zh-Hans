---
title: robots.txt未更新或显示默认设置
description: 文章提供了正确配置“robots.txt”时的解决方案，例如根据[Adobe Commerce robots.txt的最佳实践](https://support.magento.com/hc/en-us/articles/360048754931)，但“robots.txt”未更新或显示默认设置。
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt未更新或显示默认设置

这篇文章为您在配置了 `robots.txt` 正确，例如根据 [Adobe Commerce robots.txt的最佳实践](https://support.magento.com/hc/en-us/articles/360048754931) 但是 `robots.txt` 未更新或显示默认设置。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.x、2.4.x

## 问题

无法更改默认值 `robots.txt` 设置。

<u>重现问题的步骤：</u>

1. 访问管理面板。
1. 将内容添加到 **内容** >设计> **配置** > **编辑自定义指令`robots.txt`** 文件（例如文本“hello”）并保存更改。
1. 访问 `robots.txt` url。

<u>预期结果：</u>
`robots.txt` 具有保存的文本。

<u>实际结果：</u>

`robots.txt` 文件未更改。

## 原因

搜索引擎索引已关闭。

## 解决方案

启用按搜索引擎编制索引。 请参阅 [按搜索引擎配置索引](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html#configure-indexing-by-search-engine) 在我们的开发人员文档中。

## 相关阅读

* [添加站点地图和搜索引擎机器人](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 在我们的开发人员文档中。
