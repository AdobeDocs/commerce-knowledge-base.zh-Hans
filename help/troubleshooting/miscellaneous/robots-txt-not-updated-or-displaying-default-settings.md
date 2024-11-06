---
title: robots.txt未更新或显示默认设置
description: 文章提供了正确配置“robots.txt”时的解决方案，例如根据[Adobe Commerce robots.txt的最佳实践](https://support.magento.com/hc/en-us/articles/360048754931)，但“robots.txt”未更新或显示默认设置。
exl-id: 629b1247-9282-49f9-ada3-a804ddbaa0f5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# robots.txt未更新或显示默认设置

文章提供了正确配置`robots.txt`时的解决方案，例如根据[Adobe Commerce robots.txt的最佳实践](https://support.magento.com/hc/en-us/articles/360048754931)，但`robots.txt`未更新或显示默认设置。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.x、2.4.x

## 问题

无法更改默认`robots.txt`设置。

<u>要再现的步骤：</u>

1. 访问管理面板。
1. 将内容添加到&#x200B;**内容** >设计> **配置** > **编辑`robots.txt`**&#x200B;文件的自定义指令（如文本“hello”）并保存更改。
1. 访问`robots.txt` url。

<u>预期结果：</u>
`robots.txt`保存了文本。

<u>实际结果：</u>

`robots.txt`文件未更改。

## 原因

搜索引擎索引已关闭。

## 解决方案

启用按搜索引擎编制索引。 请参阅我们的开发人员文档中的[按搜索引擎配置索引](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap#configure-indexing-by-search-engine)。

## 相关阅读

* 在开发人员文档中[添加站点地图和搜索引擎机器人](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)。
