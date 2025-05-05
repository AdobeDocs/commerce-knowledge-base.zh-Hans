---
title: 提交不正确的文件时出现部署错误
description: 当您收到因不正确提交到不应添加的文件/文件夹存储库而导致的部署错误时，本文提供了此问题的解决方案。
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# 提交不正确的文件时出现部署错误

本文修复了因提交到存储库的不正确而不应添加的文件/文件夹而导致部署错误的问题。

## 受影响的产品和版本

云基础架构上的Adobe Commerce（所有版本）

## 问题

提交到文件/文件夹存储库时出现部署错误。 例如，以下错误是由于在[构建阶段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=zh-Hans#build-phase)期间尝试连接到数据库时当前不可用而导致的：

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## 原因

某些文件/文件夹不应提交到存储库，因为它们导致[部署工作流](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=zh-Hans)中断。

## 解决方案

从存储库中删除这些文件/文件夹（如果存在）：

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
