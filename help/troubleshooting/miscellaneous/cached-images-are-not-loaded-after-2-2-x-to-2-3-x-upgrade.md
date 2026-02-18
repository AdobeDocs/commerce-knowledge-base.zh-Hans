---
title: 从2.2.X升级到2.3.X后，不会加载缓存的图像
description: 本文为从Adobe Commerce on cloud infrastructure 2.2.X升级到2.3.X后无法显示缓存的图像的问题提供了解决方案。
exl-id: 3e6bd5aa-bd5d-4880-8b78-64f280647abe
feature: Cache, Upgrade
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 从2.2.X升级到2.3.X后，不会加载缓存的图像

本文为从Adobe Commerce on cloud infrastructure 2.2.X升级到2.3.X后无法显示缓存的图像的问题提供了解决方案。

## 受影响的版本和版本：

* Adobe Commerce on cloud infrastructure Pro计划架构2.2.X、2.3.X

## 问题

Adobe Commerce从2.2.X升级到2.3.X后，缓存的产品图像不可用，而是显示404页面。

问题是由于`.magento.app.yaml`中设置的Nginx配置不正确导致的： `index.php` （或none）用于`"/media"`位置而非`passthru: /get.php`。

## 解决方案

1. 在`.magento.app.yaml`位置检查您的`"/media"`配置文件。 正确的配置如下所示：

   ```yaml
   "/media":
       root: "pub/media"
       allow: true
       scripts: false
       expires: 1y
       passthru: "/get.php"
   ```

1. 如果`passthru`未设置为`"/get.php"`且未设置`expires`，请执行以下步骤。
1. 更正配置文件。
   * 入门计划：自行更正文件并推送更改。
   * 专业计划：
   * 集成：自行更正文件并推送更改。
   * 暂存和生产：自行更正文件，推送更改，然后创建[Adobe Commerce支持票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)以应用它。

1. 在Commerce管理员中启用Fastly图像优化（必须先配置Fastly），如<https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization>中所述。

如果配置正确，但仍遇到问题，请继续调查或联系[Adobe Commerce支持](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide)。
