---
title: 安装最新修补程序以修复Adobe Commerce Redis问题
description: 本文介绍[Adobe Commerce on cloud infrastructure修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)软件包中提供的与Redis相关的最新修补程序。
exl-id: 0335bc11-f679-4629-b4e7-6a0e68c3ae44
feature: Cache, Install, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 安装最新修补程序以修复Adobe Commerce Redis问题

本文介绍[Adobe Commerce on cloud infrastructure Patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)软件包中提供的与Redis相关的最新修补程序。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.3.3、2.3.4

## 问题

Redis额外的CPU和内存消耗可能会降低Adobe Commerce性能，进而降低网站的整体性能。

## 解决方案

应用Adobe Commerce on cloud infrastructure修补程序包中提供的最新修补程序。 有关详细说明，请参阅我们的开发人员文档中的[应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

Adobe Commerce在云基础架构上提供的最新Redis修补程序软件包具有以下功能：

* 减小Redis的网络通信大小
* 修复导致额外内存消耗的争用情况
* 更改缓存适配器以涵盖逐出情况
* 降低Redis CPU消耗

如果您在云基础架构2.3.3或更高版本上运行Adobe Commerce，Adobe Commerce还建议升级到Redis 5。
