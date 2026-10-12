---
title: 安装过程中，PHP日期警告
description: 本文修复了在安装期间出现PHP日期警告的问题。
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 1%
---
# 安装过程中，PHP日期警告

本文修复了在安装期间出现PHP日期警告的问题。

## 详细信息 {#details}

在安装过程中，会显示以下消息：

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### 解决方案 {#solution}

请仔细检查PHP时区设置。 请参阅我们的开发人员文档中的[安装指南> PHP设置](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)。
