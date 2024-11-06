---
title: 确保Elasticsearch安装正确
description: 本文介绍了因安装和配置不正确的Elasticsearch(ES)所导致问题的解决方案。
exl-id: d2c5971c-4db4-4857-ae79-970313bce981
feature: Install
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# 确保Elasticsearch安装正确

本文介绍了因安装和配置不正确的Elasticsearch(ES)所导致问题的解决方案。

>[!WARNING]
>
>关于Adobe Commerce on cloud infrastructure，请注意，如果没有48个工作小时的通知，服务升级无法推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产前48小时，[提交支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，其中详细列出所需的服务升级，并指明希望升级过程开始的时间。

## Elasticsearch版本与Adobe Commerce的兼容性

* Adobe Commerce内部部署和Adobe Commerce on cloud基础架构：
   * v2.2.3+支持ES 5.x
   * v2.2.8+和v2.3.1+支持ES 6.x
   * 由于[生命周期结束](https://www.elastic.co/support/eol)，不建议使用ES v2.x和v5.x。 但是，如果您使用的是Adobe Commerce v2.3.1并且要使用ES 2.x或ES 5.x，您必须[更改Elasticsearchphp客户端](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)。
* Magento Open Sourcev2.3.0+支持ES 5.x和6.x （但建议使用6.x ）。

## 问题

以下症状表示Elasticsearch配置不正确：

* `Error: No alive nodes in your cluster` — 此错误可能显示在Adobe Commerce日志中：
   * `var/log/system.log`
   * `var/log/support_report.log`
   * `var/log/cron.log`
   * `var/log/exception.log`
   * 或在提示符下（例如，当您运行重新索引时）
* 指示Elasticsearch版本与当前版本的Adobe Commerce不兼容的错误(这是特定于云基础架构的Adobe Commerce错误)：

  ```
  [YYYY-MM-DD HH:MM:SS] CRITICAL: Fix configuration with given suggestions:    - Elasticsearch version #<version> is not compatible with current version of magento    Upgrade elasticsearch version to ~5.0
  ```

其中&#x200B;*版本*&#x200B;是在云环境中运行的Elasticsearch服务。

## 原因

Elasticsearch安装不正确。 原因可能是：

* 配置文件中存在拼写错误。
* 配置文件中的某个版本与为环境安装的任何版本的Elasticsearch都不匹配。
* 已在环境中正确安装、在配置文件中正确配置的版本，但不是当前安装的Adobe Commerce版本支持的版本。

## 解决方案

要正确设置Elasticsearch，请执行以下操作：

* 云基础架构上的Adobe Commerce上的商家可以按照我们的开发人员文档中的步骤操作： [设置Elasticsearch服务](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)。
* Adobe Commerce内部部署和Magento Open Source上的商家可以按照我们的开发人员文档中的步骤操作： [安装和配置Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/search/overview-search)。

设置Elasticsearch后，请检查它是否配置正确：

1. 登录到服务器。
1. 检查运行以下命令的输出中的Elasticsearch版本号（2.x、5.x或6.x）： `curl -XGET <Elasticsearch hostname>:<Elasticsearch server port>`例如，在Adobe Commerce中云基础架构上的版本： `curl -XGET localhost:9200`
1. 通过运行以下命令检查Adobe Commerce中云基础架构配置中所配置的内容： `php bin/magento config:show catalog/search`
1. 检查`catalog/search/engine`并确保它与Elasticsearch的版本号匹配。 例如，在Adobe Commerce中，关于云基础架构：
   * Elasticsearch5.X - elasticsearch5
   * Elasticsearch6.X - elasticsearch6
   * Elasticsearch2.X - elasticsearch
1. 检查`index_prefix`。 如果您有多个环境，请确保它们具有不同的`index_prefix`值。
