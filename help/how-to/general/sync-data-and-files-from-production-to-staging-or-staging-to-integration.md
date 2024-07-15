---
title: 将数据和文件生产同步到暂存环境或暂存到集成
description: 本文说明如何在Adobe Commerce上将生产环境同步到暂存（在云基础架构上）；这是不可能的。
exl-id: e3d001d1-1b2a-41b5-9b4a-00e53dc9d001
feature: Integration, Build
source-git-commit: ef294ddc9c4a12b06ce7738cb4702253dd892f3b
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 将数据和文件生产同步到暂存环境或暂存到集成

本文说明如何在Adobe Commerce上同步您的生产环境，一直到Cloud基础架构上的暂存；这是无法通过用户界面或Magento-cloud CLI实现的。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.3.x、2.4.x

## 将数据从一个环境同步到另一个环境

要同步数据，必须手动从源环境中转储数据库。 要将数据传输到另一个环境，您必须将源转储上传到目标环境并导入它。 有关详细信息，请参阅我们的开发人员文档中的[将Adobe Commerce代码导入Cloud项目>导入Adobe Commerce数据库](https://devdocs.magento.com/cloud/setup/first-time-setup-import-import.html)。

对于云基础架构上的Adobe Commerce Pro计划架构，您还可以从暂存和生产同步到集成主分支。 此同步仅提取和推送代码，而不提取数据。 要同步数据，您需要转储数据库数据并将其推送到另一个环境的数据库。

>[!WARNING]
>
>无法在Pro Staging和Production群集中同步数据库。

## 将文件从一个环境同步到另一个环境

要将文件从一个环境同步到另一个环境，请使用`rsync`命令。 有关详细信息，请参阅我们的开发人员文档中的[部署代码并迁移静态文件和数据>使用rsync迁移文件](https://devdocs.magento.com/cloud/live/stage-prod-migrate.html#migrate-files-using-rsync)。

>[!NOTE]
>
>如果要将代码从集成同步到暂存，则必须从集成分支执行此操作。 有关步骤，请参阅我们的开发人员文档中的[从环境的父级同步](/docs/commerce-cloud-service/user-guide/project/console-branches.html#sync-an-environment)。
