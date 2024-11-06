---
title: 通过管理面板访问Web设置向导时出现404 not found错误
description: 当您尝试通过管理面板访问“Web设置向导”时遇到404“未找到”错误时，本文提供的解决方案。
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# 通过管理面板访问Web设置向导时出现404 not found错误

当您尝试通过管理面板访问“Web设置向导”时遇到404“未找到”错误时，本文提供的解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）2.3.6中已弃用Web设置向导功能，2.4.0中已移除该功能。

## 问题

使用Web设置向导安装扩展时，将显示404页。

<u>重现步骤</u>：

商家单击Web设置向导以安装新模块/集成。

<u>预期的结果</u>：

模块/集成安装。

<u>实际结果</u>：

显示404错误。

## 原因

已为Cloud Infrastructure实例上的所有Adobe Commerce禁用“Web设置向导” — 无法启用它。 必须通过Composer安装扩展。

## 解决方案

在云基础架构上的Adobe Commerce上禁用此功能。

请参阅我们的开发人员文档中的[安装、管理和升级扩展](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions)，以了解如何在我们的云基础架构上执行更新或安装Adobe Commerce的外部模块。
有关如何对Adobe Commerce内部部署执行更新或安装外部模块的信息，请参阅开发人员文档中的[快速入门安装](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/composer)。

## 相关阅读

* 请参阅我们的开发人员文档中的[安装扩展](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension)。
