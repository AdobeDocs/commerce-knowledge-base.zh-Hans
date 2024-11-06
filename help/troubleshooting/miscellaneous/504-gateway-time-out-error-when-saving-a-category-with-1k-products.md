---
title: 保存具有1k+个产品的类别时出现504网关超时错误
description: 本文针对执行大类别（1,000多种产品）操作时可能遇到的超时问题提出一种解决方案。
exl-id: 1f4b0385-215d-4d3d-8704-986c090824aa
feature: Cache, Categories, Marketing Tools, Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# 保存具有1k+个产品的类别时出现504网关超时错误

本文针对执行大类别（1,000多种产品）操作时可能遇到的超时问题提出一种解决方案。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.3.3
* Adobe Commerce内部部署2.3.3
* Magento Open Source2.3.3

## 问题

先决条件： **商店** > **配置** > **目录** > **目录** > **为产品URL使用类别路径**&#x200B;选项对于您的商店视图设置为&#x200B;*是*。

<u>重现步骤</u>

1. 在Commerce管理员中，转到&#x200B;**目录** > **类别**。
1. 打开一个大类别，如分配的产品超过1000个。
1. 将产品添加到类别。
1. 单击&#x200B;**保存类别**。

<u>预期结果：</u>

已成功保存类别。

<u>实际结果：</u>

保存进程五分钟后，将显示504网关超时错误页面。

## 原因

该进程花费的时间比服务器配置的超时时间长。

## 解决方案

禁用&#x200B;**生成“类别/产品”URL重写**&#x200B;选项将从数据库中删除所有类别/产品URL重写，并显着减少大类别操作所需的时间。

>[!WARNING]
>
>关闭此选项将导致永久删除类别/产品URL重写，并且无法恢复它们。

要禁用&#x200B;**生成“类别/产品”URL重写**&#x200B;选项：

1. 在Commerce管理员中，导航到&#x200B;**商店** > **配置** > **目录** > **目录**。
1. 在配置页面的左上角的&#x200B;**范围**&#x200B;字段中，将配置范围设置为&#x200B;*默认配置*。
1. 将&#x200B;**生成“类别/产品”URL重写**&#x200B;设置为&#x200B;*否*。
1. 单击&#x200B;**保存配置**。
1. 通过运行清理缓存    ```bash    bin/magento cache:clean    ```    或在Commerce管理员中的&#x200B;**系统** > **工具** > **缓存管理**&#x200B;下。

现在，您可以继续将产品添加到类别，或移动具有大量产品的类别，这些操作将花费更少的时间，并且不会导致超时。

## 相关阅读

我们的用户指南中的[自动产品重定向](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-redirect-product-automatic)。
