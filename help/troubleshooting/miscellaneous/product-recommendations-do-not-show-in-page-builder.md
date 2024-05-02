---
title: 页面生成器中未显示产品Recommendations
description: 本文为页面生成器中未显示“产品Recommendations”选项的问题提供了一个解决方案。
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 页面生成器中未显示产品Recommendations

本文为页面生成器中未显示“产品Recommendations”选项的问题提供了一个解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）

## 问题

页面生成器中不显示“产品Recommendations”选项。

## 原因

页面生成器中没有用于添加产品Recommendations的选项。 用于页面生成器的产品Recommendations是一个可选模块，需要单独安装。

## 解决方案

1. 通过运行以下命令检查是否已单独安装模块： `composer show magento/module-page-builder-product-recommendations`
1. 如果返回以下消息： *未找到magento/module-page-builder-product-recommendations包*，则必须通过运行以下命令来安装它： `composer require magento/module-page-builder-product-recommendations`

通过在页面生成器中启用“产品Recommendations”，您将能够 [添加推荐单位](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 添加到在页面生成器中创建的任何内容。

## 相关阅读

* [添加内容 — 产品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 在我们的用户指南中。
* [安装和配置产品Recommendations](https://devdocs.magento.com/recommendations/install-configure.html) 在我们的开发人员文档中。
* [Adobe Commerce用户指南](https://docs.magento.com/user-guide/)
