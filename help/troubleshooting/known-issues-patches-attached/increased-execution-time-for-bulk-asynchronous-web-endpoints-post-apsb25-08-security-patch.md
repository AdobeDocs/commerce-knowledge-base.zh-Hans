---
title: APSB25-08安全修补程序后，批量异步Web端点的执行时间增加
description: 本文提供了一个修补程序，用于解决在应用APSB25-08安全修补程序后，对1000多个条目的POST rest/all/async/bulk/V1/products请求执行时间显着增加的问题。
feature: Security, Cache, REST, Products, Customers
role: Admin, Developer
exl-id: 784a48cb-1ef1-432b-b09f-ebcbb9bebf01
source-git-commit: f0c2e20e0bd6dab713be59c1c686ee2948445bd4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# APSB25-08安全修补程序后，所有批量异步Web端点的执行时间都有所增加

本文为所有批量异步Web端点（例如`POST rest/all/async/bulk/V1/products`）提供了一个修补程序，这些端点具有1000多个条目，在应用APSB25-08安全修补程序后执行时间显着延长。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法） 2.4.4、2.4.4-p1、2.4.4-p2、2.4.4-p3、2.4.4-p4、2.4.4-p5、2.4.4-p6、2.4.4-p7、2.4.4-p8、2.4.4-p9、2.4.4-p10、2.4.4-p11、2.4.4-p12

* Adobe Commerce（所有部署方法） 2.4.5、2.4.5-p1、2.4.5-p2、2.4.5-p3、2.4.5-p4、2.4.5-p5、2.4.5-p6、2.4.5-p7、2.4.5-p8、2.4.5-p9、2.4.5-p10、2.4.5-p11

* Adobe Commerce（所有部署方法） 2.4.6、2.4.6-p1、2.4.6-p2、2.4.6-p3、2.4.6-p4、2.4.6-p5、2.4.6-p6、2.4.6-p7、2.4.6-p8、2.4.6-p9

* Adobe Commerce（所有部署方法） 2.4.7、2.4.7-p1、2.4.7-p2、2.4.7-p3、2.4.7-p4

* Adobe Commerce（所有部署方法） 2.4.8

## 问题

应用APSB25-08安全修补程序后，具有1000个以上条目的`POST rest/all/async/bulk/V1/products`请求的执行时间显着延长。

<u>重现步骤</u>：

1. 发出包含1000多个条目（名称、SKU和描述已足够）的`POST rest/all/async/bulk/V1/products`请求。
1. 请注意请求所用的时间。
1. 应用APSB25-08安全修补程序并使用`se:di:co`清除生成的数据和缓存。
1. 运行`bin/magento c:f`。
1. 请转到storefront以确保缓存和生成的文件已准备就绪。
1. 重复步骤1中的请求。
1. 请注意，请求所花费的时间已增加。
1. 删除APSB25-08安全修补程序，刷新缓存，重新生成代码，然后重复步骤1中的请求以确认执行时间恢复正常。 （可选）

<u>预期的结果</u>：

应用安全修补程序后，`async/bulk`请求的执行时间显着增加。

<u>实际结果</u>：

应用安全修补程序后，`async/bulk`请求的执行时间应该不会显着增加，但预计会有所增加。

## 解决方案

要解决此问题，请应用[AC-14078-2-4x-composer-patch.zip](assets/AC-14078-2-4x-composer-patch.zip)。

## 如何应用修补程序

解压缩文件，并在我们的支持知识库中参阅[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)获取相关说明。

## 相关阅读

* [可用于Adobe Commerce的安全更新 — APSB25-08](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)
