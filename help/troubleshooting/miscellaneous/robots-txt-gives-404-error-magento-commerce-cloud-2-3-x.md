---
title: robots.txt在云基础架构上显示404错误Adobe Commerce
description: 本文修复了Adobe Commerce中的“robots.txt”文件在云基础架构上引发404错误的问题。
exl-id: 6f0b9f47-1901-4c43-88d8-fd992015d70f
feature: Cloud, Marketing Tools, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# robots.txt在云基础架构上显示404错误Adobe Commerce

本文修复了`robots.txt`文件在云基础架构上的Adobe Commerce中引发404错误的情况。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 问题

`robots.txt`文件不起作用，引发了Nginx异常。 `robots.txt`文件是“动态”生成的。 `/robots.txt` URL无法访问`robots.txt`文件，因为Nginx具有重写规则，该规则强制将所有`/robots.txt`请求重定向到不存在的`/media/robots.txt`文件。

## 原因

当Nginx未正确配置时，通常会发生这种情况。

## 解决方案

解决方案是禁用将`/robots.txt`请求重定向到`/media/robots.txt`文件的Nginx规则。 启用了自助服务的商家可以自行完成此操作，而未启用自助服务的商家需要创建支持工单。

如果未启用自助服务（或不确定是否启用自助服务），请[提交Magento支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求将Nginx重定向规则从`/robots.txt`个请求删除到`/media/robots.txt`。

如果您已启用自助服务，请将ECE-Tools至少升级到2002.0.12，并在`.magento.app.yaml`文件中删除Nginx重定向规则。 有关详细信息，请参考开发人员文档中的[添加站点地图和搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap.html)。

## 相关阅读

* [如何在我们的支持知识库中阻止恶意流量进行Fastly级别](/help/how-to/general/block-malicious-traffic-for-magento-commerce-on-fastly-level.md)的Magento Commerce Cloud。
* 在开发人员文档中[添加站点地图和搜索引擎机器人](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)。
* 我们用户指南中的[搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)。
