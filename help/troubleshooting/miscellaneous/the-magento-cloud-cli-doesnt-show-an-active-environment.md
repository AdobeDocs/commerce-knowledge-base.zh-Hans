---
title: “Magento-cloud”[!DNL CLI]不显示活动环境
description: 本文介绍了一个已知的Adobe Commerce问题，该问题导致“Magento-cloud” [!DNL CLI]（命令行工具）不显示活动环境。
feature: Cloud, Integration, Configuration
role: Developer
exl-id: 3c1b5de2-8888-4531-9dc1-cd478e3c96fc
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: cc04bd17-78d5-5120-8c3d-1b8a57e49280
    internal-label: Integration
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '136'
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
