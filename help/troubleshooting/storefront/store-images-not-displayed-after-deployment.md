---
title: 部署后不显示存储映像
description: 本文为部署后图像无法正确显示提供了一个解决方案。
exl-id: 7e6bcebd-edff-437a-9103-2743443d2ed9
feature: Cache, Categories, Deploy, Storefront
role: Admin
source-git-commit: c4d586ca3980acbe4f33c5f2616ef7f3051bc7d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# 部署后不显示存储映像

本文为部署后图像无法正确显示提供了一个解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x

## 问题

在调整图像大小时使用店面主题时，图像在部署时不会显示或从目录页面中消失。

## 原因

这可能是由于从缓存加载图像而发生的。

## 解决方案

如果发生这种情况，您可以使用Magento命令重新生成图像缓存并正确显示图像。

要执行此操作，您需要通过[云控制台](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)提供的SSH信息和商店URL。

1. SSH到[数据库转储](/help/how-to/general/create-database-dump-on-cloud.md)的源项目，如开发人员文档中的[SSH到环境](https://devdocs.magento.com/guides/v2.3/cloud/env/environments-ssh.html#ssh)中所述。
1. 通过运行以下代码重新生成图像缓存：

   ```bash
   php bin/magento catalog:images:resize
   ```

1. 通过商店URL测试类别页面。
