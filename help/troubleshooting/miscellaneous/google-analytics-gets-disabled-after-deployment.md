---
title: 部署后禁用Google Analytics
description: 本主题将讨论您在部署期间可能遇到的Google Analytics典型问题的解决方案。
exl-id: ecf6a277-2dfa-45cf-b86f-9a27f39017f4
feature: Build, Deploy, Variables
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# 部署后禁用Google Analytics

本主题将讨论您在部署期间可能遇到的Google Analytics典型问题的解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

跨环境部署代码时，生成和部署脚本将验证是否已部署`master/production/staging`分支以启用Google Analytics。 在部署主环境的开发（或子）分支到开发人员环境（集成）时，部署脚本将禁用Google Analytics。

## 原因

此功能旨在确保开发人员的数据和交互不会发送给Google Analytics或由进行跟踪。

## 解决方案

如果要始终启用Google Analytics，请按照开发人员文档中的[部署变量](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#enable_google_analytics)中的说明设置部署变量`ENABLE_GOOGLE_ANALYTICS = true`。

>[!NOTE]
>
>我们知道，本文可能仍然包含行业标准的软件术语，有些人可能会认为这些术语具有种族主义、性别歧视或压迫性，并且可能会使读者感到伤害、创伤或不受欢迎。 Adobe正在努力从我们的代码、文档和用户体验中删除这些术语。
