---
title: 如何为GraphQL请求绕过WAF
description: 本文介绍了如何为GraphQL请求绕过WAF。
feature: GraphQL
exl-id: 3a0f2c22-f976-4596-b6a9-4634be1ea4c3
source-git-commit: 2bec86818336a9ef4d8316e257a0ca4256cdd93c
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# 如何为GraphQL请求绕过WAF

本文说明当[!DNL Fastly] WAF阻止您的GraphQL请求时，如何为GraphQL请求绕过WAF。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 原因

由于GraphQL请求的内在性质，可能会有很多重复字符触发[!DNL Fastly] WAF阻止请求的误报。

## 解决方案

1. 通过[!DNL Fastly]Magento模块添加自定义代码片段，绕过这些请求的WAF：

   类型： recv
优先级：15
内容：

   ```
   if( req.url.path ~ "^/graphql" ) {
       set req.http.bypasswaf = "1";
   }
   ```

1. 单击&#x200B;**[!UICONTROL Upload VCL to Fastly]**。

## 相关阅读

* 云基础架构指南上的Commerce中的[Web应用程序防火墙(WAF)](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service)。
* 在Commerce on Cloud Infrastructure指南中[自定义VCL入门](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets)。
