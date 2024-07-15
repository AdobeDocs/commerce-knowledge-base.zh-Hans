---
title: 在Adobe Commerce上重新排列云分支
description: 本文提供了在Adobe Commerce上重新排列云分支的步骤（如果这些分支未按照正确的层次结构组织）。 如果没有将分支组织在正确的层次结构中，则无法合并到正确的父分支 — 它将转到现有的父分支。
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 在Adobe Commerce上重新排列云分支

本文提供了在Adobe Commerce上重新排列云分支的步骤（如果这些分支未按照正确的层次结构组织）。 如果没有将分支组织在正确的层次结构中，则无法合并到正确的父分支 — 它将转到现有的父分支。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce，2.3.0-2.3.7-p2、2.4.0-2.4.3-p1

## 云分支组织

分支的正确层次结构组织为：

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## 针对不正确的云分支组织的解决方案

要重新排列云分支，请执行以下操作：

1. 您必须具有[[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)角色。
1. 安装magento-cloud [!DNL CLI]（如果尚未安装）。
1. 为需要移动的分支运行以下命令：
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

注意：创建新分支时，可以指定父分支。 有关步骤，请参阅我们的开发人员文档中的[创建分支快速入门](https://devdocs.magento.com/cloud/env/environments-start.html#getstarted)。

您可以使用`branch <environment-name> <parent-environment-ID>` magento-cloud环境命令创建新的环境分支。

创建和激活新环境分支可能需要额外的时间。

## 相关阅读

在我们的开发人员文档中，[使用 [!DNL CLI]](https://devdocs.magento.com/cloud/env/environments-start.html)管理分支。
