---
title: Extension Manager在Adobe Commerce 2.3.x中不显示扩展
description: 在通过Commerce Marketplace购买扩展后，本文为Adobe Commerce 2.3.x中的管理员Extension Manager中缺少扩展提供了解决方法。
exl-id: bed8506d-39b9-449a-891b-466d214a0fe8
feature: Extensions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Extension Manager在Adobe Commerce 2.3.x中不显示扩展

在通过Commerce Marketplace购买扩展后，本文为Adobe Commerce 2.3.x中的管理员Extension Manager中缺少扩展提供了解决方法。

## 受影响的产品和版本

* Adobe Commerce版本（所有部署方法）2.3.x

## 问题

当您通过Commerce Marketplace购买扩展时，无法使用核心Adobe CommerceExtension Manager安装它们。 当您添加访问密钥并同步到Marketplace时，Extension Manager不会显示任何扩展。

此问题的&#x200B;**解决方法**&#x200B;是使用命令行Adobe Commerce安装，如开发人员文档中的[常规CLI安装](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/extensions)中所示。

<u>重现步骤</u>：

1. 通过Commerce Marketplace购买扩展。
1. 添加扩展的访问密钥并同步到Marketplace。
1. 转到管理员的Extension Manager部分。

<u>预期的结果</u>：

该扩展将显示在Commerce管理员的Extension Manager部分中。

<u>实际结果</u>：

**Commerce管理员的Extension Manager部分上未显示任何扩展，类似于以下图像：**


![KB-607_Image_1.png](assets/KB-607_Image_1.png)

## 解决方法

使用命令行Adobe Commerce安装，如开发人员文档中的[常规CLI安装](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/extensions)中所示。
