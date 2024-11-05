---
title: 登录到Commerce管理员后出错
description: 本文提供了针对该问题的解决方案，您将收到一则错误消息，指出在此服务器上未找到所请求的URL。
exl-id: f52b383b-87f2-4216-9bf4-e765db31ca6b
feature: Admin Workspace
role: Developer
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# 登录到Commerce管理员后出错

本文提供了针对该问题的解决方案，您将收到一则错误消息，指出在此服务器上未找到所请求的URL。

## 详细信息

在此服务器上未找到请求的URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/。

请注意，URL中缺少介于`magento2`和`index.php`之间的斜杠字符。

## 解决方案

基本URL不正确。 基本URL必须：

* 以`http://`或`https://`开头
* 以斜杠( `/` )结尾
* 匹配`core_config_data`数据库表中`web/unsecure/base_url`记录的大小写

请使用有效值重新运行安装。

## 相关阅读

[在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
