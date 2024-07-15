---
title: 禁用模块后出现问题
description: 本文为在Commerce管理员中禁用模块输出后的模块功能问题提供了解决方案。
exl-id: 517f6993-f09e-4a94-8c57-175ecf9a98a8
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# 禁用模块后出现问题

本文为在Commerce管理员中禁用模块输出后的模块功能问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.1.X或更早版本
* Adobe Commerce内部部署2.1.X或更低版本

## 问题

在Commerce管理员的&#x200B;**存储** > **设置** > **配置** >高级> **高级**&#x200B;下禁用了模块输出，您可能会开始看到与模块功能相关的问题。

## 原因

在&#x200B;**存储** > **设置** > **配置** >高级> **高级**&#x200B;下禁用模块输出，仅禁用输出(HTML、JS)，但不会禁用此模块的功能。

## 解决方案

如果需要禁用模块功能，请按照开发人员文档中的[启用或禁用模块](https://devdocs.magento.com/guides/v2.1/install-gde/install/cli/install-cli-subcommands-enable.html)中的说明禁用模块。

模块输出禁用功能已从版本2.2.0中删除。
