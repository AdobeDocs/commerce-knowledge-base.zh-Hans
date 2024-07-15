---
title: “Magento — 云” [!DNL CLI] 未显示活动环境
description: 本文介绍了一个已知的Adobe Commerce问题，“Magento-cloud” [!DNL CLI] （命令行工具）不显示活动环境。
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
source-git-commit: 5eac8bb54e205eff6a96e279295cd12db1009f0a
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 0%

---

# `Magento-cloud` [!DNL CLI]未显示活动环境

## 问题

有多个活动环境，您正在尝试通过运行`Magento-cloud` [!DNL CLI] （命令行工具）命令与环境交互。 （例如： `ssh`、`db:size`、`db:sql`等）
但是，提示选择所需环境时不会列出此环境。 （例如：集成环境）

```
Enter a number to choose an environment:
Default: master
  [0] integration2 (type: development)
  [1] master (type: development)
  [2] production
  [3] staging
 >
```

## 原因

由于部署正在进行、停滞或失败，环境可能不可用。

## 解决方案

您将需要手动使用`e|-environment`标志指定环境。

1. 查找活动环境的列表并记下环境名称：

```
$ magento-cloud environment: list |grep "Active\|ID"
Your environments are:

| ID                     | Title            | Status       | Type           |
| Master                 | Master           | Active       | Development    |
|   Production           | Production       | Active       | Production     |
|     Staging            | Staging          | Active       | Staging        |
|       Integration      | Integration      | Active       | Development    |
|          Integration 2 | Integration 2    | Active       | Development    |
```

2.使用命令指定环境的ID：

`magento-cloud ssh -e integration`
