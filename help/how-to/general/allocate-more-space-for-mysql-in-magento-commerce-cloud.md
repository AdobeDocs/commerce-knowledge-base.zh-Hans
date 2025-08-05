---
title: 在云上的Adobe Commerce中为MySQL分配更多空间
description: 本文介绍了如何在云基础架构的Adode Commerce中为MySQL分配更多空间。
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 139c2836ba36686357c7a5458a36550c7b1273c1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# 在云上的Adobe Commerce中为MySQL分配更多空间


## 在入门计划和专业计划集成上分配空间

对于所有入门计划环境和Pro计划[集成环境](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242)，您可以通过增加`.magento/services.yaml`参数在`mysql: disk:`文件中为MySQL分配更多空间。 例如：

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

请参阅[设置MySQL服务](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql)文章以供参考。

更改`.magento/services.yaml`文件后，您需要提交并推送更改以便应用。 推送将触发部署过程。

>[!WARNING]
>
>Starter计划分区绝不应该缩小（例如，从30GB扩展到20GB），因为这可能会导致灾难性数据损坏。

## 在Pro计划暂存或生产环境中分配空间

要对Pro计划的暂存或生产环境进行这些更改，必须创建[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)。 在提交支持票证以增加存储时，支持人员需要知道存储应该应用到（`/mysql`或`/exports`）的多少，以及应该应用到哪个分区。 存储增加请求需要Adobe客户团队的批准，该团队将在批准前审核您授权的存储量（根据订购单）。

## 减少分配空间不可用（专业版和入门版计划）

Adobe Commerce支持可以增大分区（`/mysql`或`/exports`），但不能收缩分区。 这样做可能会造成数据损坏，因此不能减少分区的存储。
对于“入门”计划也是如此，您可以自行增加分配的空间：强烈不建议降低，这可能会导致灾难性数据损坏。
