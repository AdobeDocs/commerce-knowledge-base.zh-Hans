---
title: 将适用于Adobe Commerce on cloud的MariaDB 10.0升级到10.2
description: MariaDB 10.0和10.1已终止生命周期(EOL)。 [支持分别于2019年3月31日和2020年10月17日结束](https://endoflife.date/mariadb)。 本文说明如何将MariaDB从10.0升级到10.2，或从10.2升级到10.3或升级到10.4，以便在云基础架构上使用Adobe Commerce。
exl-id: bf66798b-f05c-482f-a2b4-b9bef92b0bab
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 将适用于Adobe Commerce on cloud的MariaDB 10.0升级到10.2

MariaDB 10.0和10.1已终止生命周期(EOL)。 [支持分别于2019年3月31日和2020年10月17日结束](https://endoflife.date/mariadb)。 本文说明如何将MariaDB从10.0升级到10.2，或从10.2升级到10.3或升级到10.4，以便在云基础架构上使用Adobe Commerce。

>[!NOTE]
>
>MariaDB 10.0生命周期结束(EOL)，当前Adobe Commerce版本不支持它。 最佳实践是在任何EOL版本生命周期结束后的30天内停止使用该版本。

## 受影响的产品和版本

* 对于Adobe Commerce on cloud infrastructure 2.3.x，建议使用MariaDB 10.2。
* 对于2.4.x，建议使用MariaDB 10.4。MariaDB 10.3还与Adobe Commerce on cloud infrastructure 2.4.x兼容。

## 升级步骤

要从MariaDB 10.0升级到10.2、从10.2升级到10.3或升级到10.4，请完成以下步骤：

1. 使用ECE-Tools DB备份命令](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)创建[数据库备份。 如果更新表/行时出现问题，必须在步骤2和3之前执行此操作。
1. [检查所有压缩表并将其转换为动态表](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.html)。 这是为避免在数据库升级期间潜在的数据丢失所必需的。
1. 检查MYISAM表。 您需要[将所有MyISAM表转换为InnoD](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)。
1. 准备数据库表和行（前两步）后，使用ECE-Tools DB备份命令创建[DB备份](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)。
1. [打开支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以计划从MariaDB 10.0升级到10.2、从10.2升级到10.3或10.4。在票证中详细说明了您希望升级数据库的日期和时间。 支持团队需要48小时通知，并且商家开发团队需要可用。 在同意升级的时间和日期后，执行以下操作：
   1. 将您的网站置于维护模式，并停止任何DB活动，例如cron。
   1. 使用ECE-Tools DB备份命令](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)创建[数据库备份。
   1. 让支持人员知道您已完成备份。 通过您的支持票证执行此操作。 要获取查看和跟踪票证的步骤，请参阅我们的支持知识库中的[Adobe Commerce帮助中心用户指南：跟踪您的票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#track-tickets)。
   1. Adobe Commerce支持团队将开始MariaDB升级过程。 如果已经执行了上述所有步骤，并且数据库为平均大小，那么可以在大约一小时内完成此操作。 较大的数据库需要较长时间。 升级完成后，您将通过票证收到通知。
1. 禁用维护模式。 请参阅我们的开发人员文档中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。

## 相关阅读

要了解有关Adobe Commerce 2.4.x要求的更多信息，请参阅我们的开发人员文档中的[Adobe Commerce 2.4系统要求>数据库](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements#database)。
