---
title: “[!DNL Fastly]源遮盖启用常见问题解答”
description: 此常见问题解答讨论了Adobe Commerce中有关 [!DNL Fastly] 源遮盖支持的常见问题（截至2021年已完全实施）。
exl-id: d608abe7-7d64-44ce-bea1-34b201c29113
source-git-commit: 1021a1ab81481f92e850bd49330f1742fe9a21f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# [!DNL Fastly]源遮蔽启用常见问题解答

此常见问题解答讨论了有关Adobe Commerce中支持[!DNL Fastly]源遮盖的常见问题（截至2021年已完全实施）。

## 什么是[!DNL Fastly]源遮蔽？

源遮蔽是一项安全功能，它允许云基础架构上的Adobe Commerce阻止任何[!DNL non-Fastly]流量(为了防止DDoS攻击，阻止流向云基础架构（源）)。

## 隐瞒原产地有什么好处？

原始遮盖旨在防止流量绕过[!DNL Fastly Web Application Firewall] (WAF)并通过严格定义的&#x200B;**[!DNL Fastly]** > **负载平衡器** > **实例**&#x200B;流路由它。 通过此实施，所有流量均可保证通过[!DNL Fastly] WAF以及内置于负载平衡器中的内部WAF。

## 为什么这种起源掩盖会发生？

这项功能最初是为了在云基础架构上让Adobe Commerce受益而创建的。

## 我是否需要请求为项目启用源遮蔽？

不适用。 此功能应该已在所有云项目上实施，并且自2021年以来配置的任何项目默认情况下都将启用此功能。

## 来源遮蔽是否会更改传出IP地址？

不，它没有。

## 源遮盖是否会影响REST API？

[!DNL Fastly]不缓存API调用，因此客户端应该可以适应此更改。 源位置遮盖只会阻止直接转到源位置的请求，例如：

* 生产

```php
mywebsite.com.c.abcdefghijkl.ent.magento.cloud
```

* 暂存

```php
mcstaging2.mywebsite.com.c.abcdefghijkl.dev.ent.magento.cloud
```

* 暂存X

```php
mcstagingX.mywebsite.com.c.abcdefghijkl.X.dev.ent.magento.cloud
```

在此示例中，如果客户端将URL更改为``mywebsite.com``，则他们仍可以点击API：

```php
mywebsite.com/rest/default/V1/integration/admin/token?username=XXXX&password=XXXXX;
mywebsite.com/rest/default/V1/orders/
mywebsite.com/rest/default/V1/products/
mywebsite.com/rest/default/V1/inventory/source-items
```

## 此更改是否会影响部署和停机时间？

否，此更改将&#x200B;**不**&#x200B;影响部署和停机时间。

## 如果项目具有多个暂存环境，原始遮盖是否会应用于所有暂存环境？

可以，如果项目有多个暂存环境，则更改将应用于所有暂存环境。
