---
title: 部署错误： *下载……端口443时出现错误7：连接被拒绝*
description: 本文提供了针对部署错误的解决方案：*“下载时出错7 ...端口443：连接被拒绝”*。
exl-id: 520cf50f-3682-441d-87a7-8e05301a2b0c
feature: Cache, Deploy
role: Developer
source-git-commit: c005409900021a72d73c10a2df5f23be3f2bc2cf
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# 部署错误： *下载时发生错误7...端口443：连接被拒绝*

本文修复了部署失败并出现以下错误消息的问题：

```bash
W: In CurlDownloader.php line 370:
W:
W:   curl error 7 while downloading https://repo.packagist.org/p2/magento/module
W:   -sitemap.json: Failed to connect to repo.packagist.org port 443: Connection
W:    refused
```

## 受影响的版本

云基础架构上的Adobe Commerce，[所有支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

部署失败，出现&#x200B;**curl错误7**&#x200B;消息。

<u>重现步骤</u>：

触发部署。

<u>预期行为</u>：

部署成功。

<u>实际行为</u>：

部署失败，并且以下错误：下载时出现&#x200B;*curl错误7...端口443：连接被拒绝*&#x200B;显示在部署日志中。

## 原因

这可能是由于与存储库的缓存连接丢失所致。

## 解决方案

要求项目中的超级用户运行此命令：

```bash
magento-cloud project:clear-build-cache -p <project ID>
```

要检查项目上的谁是超级用户，请参阅《云基础架构上的Commerce指南》中的[查看用户的项目角色](/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=en#view-a-user’s-project-role)。

## 推荐阅读

* [Adobe Commerce部署疑难解答程序](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-29640)。
* 无法访问云存储库上的[Adobe Commerce：部署](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)时出现403禁止或404未找到错误。
* [部署失败，并显示“生成项目时出错：生成挂接失败，状态代码为1”](/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-fails-with-error-building-project-the-build-hook-failed-with-status-code-1.html)。
