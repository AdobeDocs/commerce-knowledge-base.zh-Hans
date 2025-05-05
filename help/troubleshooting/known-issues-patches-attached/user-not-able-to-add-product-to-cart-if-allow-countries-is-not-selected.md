---
title: 如果未在允许国家/地区中选择任何内容，则用户无法将产品添加到购物车
description: 本文为带有PHP 8.1的已知Adobe Commerce 2.4.4问题提供了一个修补程序，该问题导致如果未选择“允许国家/地区”，用户无法将产品添加到购物车。
exl-id: d05d1956-de23-496c-9234-c461a3cfdf36
feature: Orders, Products, Shopping Cart
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# 如果未在允许国家/地区中选择任何内容，则用户无法将产品添加到购物车

本文为带有PHP 8.1的已知Adobe Commerce 2.4.4问题提供了一个修补程序，该问题导致如果未选择“允许国家/地区”，用户无法将产品添加到购物车。

## 受影响的产品和版本

带有PHP 8.1的Adobe Commerce 2.4.4

## 问题

如果未选择允许国家/地区，则用户无法将产品添加到购物车。

<u>重现步骤</u>：

1. 登录到Commerce管理员。
1. 转到&#x200B;**商店** > **配置** > **常规** > **国家/地区选项**
1. 取消选择&#x200B;**允许国家/地区**&#x200B;字段中的所有选项。
1. 单击&#x200B;**保存配置**&#x200B;以保存配置。
1. 转到店面，尝试将产品添加到购物车。

<u>预期结果：</u>

您可以将产品添加到购物车。

<u>实际结果：</u>

您无法将产品添加到购物车。 您收到以下控制台错误：

```bash
Failed to load resource: the server responded with a status of 400 (Bad Request)
customer-data.js:87 Uncaught Error: [object Object]
    at Object.<anonymous> (customer-data.js:87:23)
    at fire (jquery.js:3500:50)
    at Object.fireWith [as rejectWith] (jquery.js:3630:29)
    at done (jquery.js:9798:30)
    at XMLHttpRequest.<anonymous> (jquery.js:10057:37)
```

## 原因

当多选配置没有任何选定项时，Adobe Commerce配置将检索`null`。 如果在8.1之前的PHP版本中进一步成功处理此配置。但是，在PHP 8.1中，由于“[Deprecate将null传递给PHP 8.1](https://wiki.php.net/rfc/deprecate_null_to_scalar_internal_arg)中内部函数的不可为空的参数”导致的错误，它无法正常工作。

## 解决方案

要解决此问题，请应用以下修补程序：

[AC-2655_2.4.4.patch.zip](assets/AC-2655_2.4.4.patch.zip)

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 有用的链接

在开发人员文档中，[将自定义修补程序应用到云基础架构上的Adobe Commerce](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。
