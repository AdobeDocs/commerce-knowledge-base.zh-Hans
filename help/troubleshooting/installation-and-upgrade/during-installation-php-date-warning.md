---
title: 安装过程中，PHP日期警告
description: 本文修复了在安装期间出现PHP日期警告的问题。
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# 安装过程中，PHP日期警告

本文修复了在安装期间出现PHP日期警告的问题。

## 详细信息 {#details}

在安装过程中，会显示以下消息：

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### 解决方案 {#solution}

请仔细检查PHP时区设置。 请参阅我们的开发人员文档中的[安装指南> PHP设置](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/php-settings.html)。
