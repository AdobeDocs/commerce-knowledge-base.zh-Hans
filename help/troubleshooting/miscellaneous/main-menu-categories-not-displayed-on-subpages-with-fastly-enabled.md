---
title: 启用Fastly的子页面上不显示主菜单（类别）
description: 本文修复了在启用Fastly或Varnish时，子页面（例如，*blog/page*）的店面未显示主菜单(或用户指南中的[类别顶部导航菜单](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html))的问题。
exl-id: 7c54791d-8aa6-4f01-a28b-a7aecdb8ff74
feature: Categories, Marketing Tools
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# 启用Fastly的子页面上不显示主菜单（类别）

本文修复了在启用Fastly或Varnish时，主菜单（或用户指南中的[类别顶部导航菜单](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html)）未显示在子页面（例如，*博客/页面*）的店面中的问题。

**原因：**&#x200B;页面的&#x200B;*URL键*&#x200B;参数中不允许的`/`字符（斜杠）（搜索引擎优化设置）。 如果错误地指定了&#x200B;*URL路径*（包含整个页面位置），而不是&#x200B;*URL键*，则通常会添加该字符：例如&#x200B;*blog/page\_name*，而不是仅指定&#x200B;*page\_name*。

**解决方案：**&#x200B;删除`/`字符（斜杠）；对于&#x200B;*URL键*&#x200B;参数，仅指定页面名称。

## 受影响的版本

* Adobe Commerce内部部署2.X.X
* 云基础架构上的Adobe Commerce 2.X.X
* Fastly或Varnish

## 问题

启用Fastly或其他基于Varnish的服务时，子页面的店面不会显示主菜单（也称为用户指南中的[类别顶部导航菜单](/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html)）。

## 原因

该问题是由添加到&#x200B;*URL键*&#x200B;参数（搜索引擎优化设置）中的不允许的`/`字符（斜杠）引起的。

如果错误地指定了&#x200B;*URL路径*（包含整个页面位置，包括页面的父资源/目录），而不是&#x200B;*URL键*，则通常会添加该字符：例如&#x200B;*blog/page\_name*，而不仅仅是&#x200B;*page\_name*。

用于SEO设置的![URL密钥参数](assets/seo_url_key.png)

## 解决方案

从存储区所有页面的&#x200B;*URL键*&#x200B;参数中删除`/`字符（斜杠）。

换言之，使用&#x200B;*URL键*&#x200B;而不是&#x200B;*URL路径*：仅提及不含父资源/目录的页面名称。

### 页面层级和SEO上的Recommendations

要设置页面层次结构，请使用“编辑页面”菜单的&#x200B;**层次结构**&#x200B;部分。

![层次结构设置](assets/hierarchy_hr.png)

您还可以使用&#x200B;**Content** > **Elements** > **Hierarchy**&#x200B;菜单 — 用于更复杂的层次结构解决方案。

对于产品页面上的SEO，请使用URL重写（**营销** > **SEO和搜索** > **URL重写**）。

## 我们用户指南中的更多信息

SEO的&#x200B;*URL键*&#x200B;参数：

* [搜索引擎优化](/docs/commerce-admin/catalog/categories/create/categories-search-engine-optimization.html)
* [添加新页面](/docs/commerce-admin/content-design/elements/pages/page-add.html)

页面层次结构：

* [概述](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html)
* [添加节点](/docs/commerce-admin/content-design/elements/pages/page-hierarchy.html#add-a-hierarchy-node)
