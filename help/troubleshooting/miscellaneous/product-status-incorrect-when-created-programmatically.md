---
title: 以编程方式创建时产品状态不正确
description: 本文修复了当产品状态为禁用且产品未显示在商店前端时，或通过编程方式创建/更新时，产品被分配给错误商店视图的问题。
exl-id: ac02f961-f9e2-4620-839f-b8dbd0befb15
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# 以编程方式创建时产品状态不正确

本文修复了当产品状态为禁用且产品未显示在商店前端时，或通过编程方式创建/更新时，产品被分配给错误商店视图的问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.X.X
* Adobe Commerce内部部署2.X.X

## 问题

当从引导了Adobe Commerce应用程序的脚本以编程方式创建或更新目录产品时，产品可能处于“已禁用”状态和/或分配给错误的存储视图。

## 原因

由于为Adobe Commerce实例管理员角色设置的ACL限制，可能出现此问题。 对于引导应用程序，将不会有具有适当ACL设置的初始化管理会话。 这将导致`Magento_AdminGws`模块中的验证失败，该模块负责检查此类操作的权限。

## 产品状态不正确的解决方案

为`Magento\Framework\Authorization\PolicyInterface`设置动态DI首选项，如开发人员文档中的[ObjectManager>程序化产品更新](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/object-manager.html#programmatic-product-updates)主题中所述。

## 相关阅读

* [Github：无法更改使用productRepository](https://github.com/magento/magento2/issues/5664)创建的产品的产品状态
