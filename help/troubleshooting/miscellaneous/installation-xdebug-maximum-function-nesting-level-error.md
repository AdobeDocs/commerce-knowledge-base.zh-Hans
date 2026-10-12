---
title: 安装xdebug最大函数嵌套级别错误
description: 本文修复了安装期间出现的xdebug最大函数嵌套级别错误。
exl-id: 1f64a9bb-59a7-41df-92a4-890d9d32bcbe
feature: Install
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 0%
---
# 安装xdebug最大函数嵌套级别错误

本文修复了安装期间出现的xdebug最大函数嵌套级别错误。

## 详细信息

在Adobe Commerce安装过程中，会显示一条与以下内容类似的消息：

`PHP Fatal error: Maximum function nesting level of '100' reached, aborting! in <path>/ClassLoader.php`

强烈建议不要在生产环境中使用`xdebug`！

## 解决方案

`xdebug`存在已知问题，该问题可能会影响Adobe Commerce安装或在安装后访问店面或Commerce管理员。

有关详细信息，请参阅我们的支持知识库中的[xdebug的已知问题](/help/troubleshooting/miscellaneous/known-issues-that-affect-installation.md)。
