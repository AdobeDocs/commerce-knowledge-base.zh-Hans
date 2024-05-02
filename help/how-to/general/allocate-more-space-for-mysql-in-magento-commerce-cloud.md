---
title: 在云上的Adobe Commerce中为MySQL分配更多空间
description: 本文介绍了如何在云基础架构的Adode Commerce中为MySQL分配更多空间。
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 在云上的Adobe Commerce中为MySQL分配更多空间


## 在入门计划和专业计划集成上分配空间

适用于所有入门计划环境和专业计划 [集成环境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)中，您可以为MySQL分配更多空间 `.magento/services.yaml` 文件，通过增加 `mysql: disk:` 参数。 例如：

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

请参阅 [设置MySQL服务](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_services-mysql.html) 供参考。

一旦您更改了 `.magento/services.yaml` 文件，您需要提交并推送更改以便应用。 推送将触发部署过程。

>[!WARNING]
>
>Starter计划分区绝不应该缩小（例如，从30GB扩展到20GB），因为这可能会导致灾难性数据损坏。

## 在Pro计划暂存或生产环境中分配空间

要对Pro计划的暂存或生产环境进行这些更改，必须创建 [支持服务单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). 在提交支持工单以增加存储时，支持人员需要知道存储应该应用于多少分区，以及应该应用于哪个分区(`/mysql` 或 `/exports`)。 存储增加请求需要您的Adobe客户团队批准，他们将在批准前审核您授权的存储量（根据订购单）。

## 减少分配空间不可用（专业版和入门版计划）

Adobe Commerce支持部门可以增加分区(`/mysql` 或 `/exports`)，但无法收缩分区。 这样做可能会造成数据损坏，因此不能减少分区的存储。
对于“入门”计划也是如此，您可以自行增加分配的空间：强烈不建议降低，这可能会导致灾难性数据损坏。
