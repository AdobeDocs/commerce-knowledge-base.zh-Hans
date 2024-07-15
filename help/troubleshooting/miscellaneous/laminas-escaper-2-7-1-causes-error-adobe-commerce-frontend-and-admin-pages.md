---
title: laminas/laminas-escaper 2.7.1导致Adobe Commerce前端和管理页面错误
description: 本文为laminas/laminas-escaper：2.7.1的发布破坏了Adobe Commerce在产品管理、类别和产品页面中的功能的问题提供了解决方案。 此问题将在Adobe Commerce 2.4.3中修复。
exl-id: 89de6827-7b90-4f08-92fb-56ed31ae2672
feature: Admin Workspace, Categories
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# laminas/laminas-escaper 2.7.1导致Adobe Commerce前端和管理页面错误


## 受影响的产品和版本

* Cloud Architecture 2.3.5+上的Adobe Commerce
* Adobe Commerce 2.3.5+

## 问题

更新laminas/laminas-escaper：2.7.1后，页面上会显示错误消息。

<u>重现步骤</u>：

将laminas/laminas-escaper更新为2.7.1。

<u>预期的结果</u>：

没有错误。

<u>实际结果</u>：

更新到laminas/laminas-escaper：2.7.1后，产品编辑（或产品管理）页面上显示一条错误消息： *TypeError： rawurlencode()预期参数1为字符串，int在/var/www/magento/vendor/laminas/laminas-escaper/src/Escaper.php：246*中提供
此错误发生在前端和管理员页面上，导致页面内容扭曲。

## 原因

laminas/laminas-escaper 2.7.1已开始对Escaper类使用严格类型验证。

## 解决方案

在每个项目的根目录中运行`composer require laminas/laminas-escaper:2.7.0`。

## 相关阅读

laminas文档： [laminas-escaper](https://docs.laminas.dev/laminas-escaper/)
