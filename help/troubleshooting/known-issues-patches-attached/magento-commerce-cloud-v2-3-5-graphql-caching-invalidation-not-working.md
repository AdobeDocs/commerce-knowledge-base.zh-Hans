---
title: Adobe Commerce on cloud infrastructure v2.3.5GraphQL缓存失效不起作用
description: 本文修复了GraphQL“GET”请求在客户更改产品信息时返回过期信息的问题。
exl-id: 10ae52bd-e71a-42e3-9600-7a9713903815
feature: GraphQL, Cache, Categories, Cloud, Paas
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Adobe Commerce on cloud infrastructure v2.3.5GraphQL缓存失效不起作用

本文针对GraphQL `GET`请求在客户更改产品信息时返回过期信息的问题提供了修补程序。

## 受影响的产品和版本

云基础架构上的Adobe Commerce v2.3.5。

## 问题

Fastly缓存GraphQL请求，并为来自Fastly的每个后续请求检索缓存的版本。 在Adobe Commerce后端中重新保存产品时，Fastly缓存应在更新产品时失效。 但是，它仍然有效。

<u>重现步骤</u>：

1. 触发以下GraphQL请求以获取特定类别的产品，例如：
   <pre><magento2-server>
    </pre>
1. 在Commerce管理中重新保存上述请求检索到的产品之一。
1. 再次触发请求。

<u>预期的结果</u>：

`X-Cache`标头包含`MISS`。

<u>实际结果</u>：

`X-Cache`标头包含`HIT`，这意味着响应已缓存。

## 解决方案

使用本文中提供的修补程序禁用GraphQL产品缓存。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[MDVA-28559\_EE\_2.3.5-p1\_COMPOSER\_v1.patch](assets/MDVA-28559_EE_2.3.5-p1_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce v2.3.5

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce v2.4.0
* Adobe Commerce内部部署v2.4.0
* 云基础架构上的Adobe Commerce v2.3.5-p2
* Adobe Commerce内部部署v2.3.5-p2
* 云基础架构上的Adobe Commerce v2.3.5-p1
* Adobe Commerce内部部署v2.3.5-p1
* Adobe Commerce内部部署v2.3.5
* 云基础架构上的Adobe Commerce v2.3.4-p2
* Adobe Commerce内部部署v2.3.4-p2
* 云基础架构上的Adobe Commerce v2.3.4
* Adobe Commerce内部部署v2.3.4
* Adobe Commerce内部部署v2.3.3-p1
* Adobe Commerce内部部署v2.3.3

## 如何应用修补程序

有关如何应用编辑器修补程序的说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
