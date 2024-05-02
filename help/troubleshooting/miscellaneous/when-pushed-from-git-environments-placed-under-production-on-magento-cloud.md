---
title: 从Git推送时处于生产状态的新环境
description: 本文为从Git版本控制系统推送新环境时将其放在Adobe Commerce上的生产环境下的问题提供了解决方案。
exl-id: 279cd6d8-fd45-45ba-8456-8b397a01976f
feature: Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 从Git推送时处于生产状态的新环境

本文为从Git版本控制系统推送新环境时将其放在Adobe Commerce上的生产环境下的问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce， [所有受支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## 问题

<u>先决条件</u>：

让本地Git控制项目克隆。

<u>重现问题的步骤</u>：

您需要从暂存分支创建集成分支：

1. 通过在本地shell中运行以下命令切换到暂存分支： `git checkout staging`
1. 通过在本地shell中运行以下命令，从暂存分支创建集成分支： `git checkout -b <branch>`
1. 通过将分支推送到远程存储库并设置上游分支，方法是在本地shell中运行以下命令： `git push --set-upstream origin <branch>`

<u>预期结果</u>：

新分支在暂存分支下创建。

<u>实际结果</u>：

新分支在生产分支下创建。

## 原因

这不是错误。 要设置其他分支的父分支，商家应使用magento-cloud CLI。

## 解决方案

只有在商家推送并激活新创建的分支后，才能设置父分支。 请参阅 [云基础架构上的Adobe Commerce >比特桶集成](https://devdocs.magento.com/cloud/integrations/bitbucket-integration.html#create-a-new-cloud-branch) 在我们的开发人员文档中。

要更新服务器上现有分支的父分支，请使用 `magento-cloud environment:info` magento-cloud CLI中的命令。

使用示例：

`magento-cloud environment:info parent Staging`

这将为当前签出的分支将父分支设置为“暂存”。

## 相关阅读

* [云基础架构上的Adobe Commerce > magento-cloud CLI](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html) 在我们的开发人员文档中。
