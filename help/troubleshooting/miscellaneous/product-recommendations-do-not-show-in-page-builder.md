---
title: 页面生成器中未显示产品Recommendations
description: 本文为页面生成器中未显示“产品Recommendations”选项的问题提供了一个解决方案。
exl-id: e96a446b-2e64-47a6-ac1b-e73183da9fb8
feature: Page Builder, Configuration, Personalization, Products, Recommendations
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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
1. 如果它返回以下消息： *找不到Package magento/module-page-builder-product-recommendations*，则必须通过运行命令来安装它： `composer require magento/module-page-builder-product-recommendations`

通过在页面生成器中启用“产品Recommendations”，您将能够[向页面生成器中创建的任何内容添加推荐单元](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html?lang=zh-Hans)。

## 相关阅读

* 在我们的用户指南中[添加内容 — 产品Recommendations](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html?lang=zh-Hans)。
* 在我们的开发人员文档中[安装和配置产品Recommendations](https://experienceleague.adobe.com/zh-hans/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure)。
* [Adobe Commerce用户指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/user-guides/home)
