---
title: 将适用于Adobe Commerce on cloud的MariaDB 10.4升级到10.5
description: MariaDB 10.4将于2024年6月18日停止支持。 本文介绍如何将MariaDB从10.4升级到10.5，以继续在云基础架构上使用Adobe Commerce。
feature: Best Practices, Cloud
exl-id: 065840b8-28c1-4686-95fc-df3e73152845
source-git-commit: 9e218e3fadbf9941c94d309fcfb6f258d2f4faf2
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# 将适用于Adobe Commerce on cloud的MariaDB 10.4升级到10.5

MariaDB是与Adobe Commerce一起使用的企业开源数据库。

MariaDB 10.4将于[2024年6月18日](https://endoflife.date/mariadb)终止支持。 如果您使用不受支持的MariaDB版本，则不再符合PCI规范。 本文介绍了如何从MariaDB 10.4升级到10.5，以继续在云基础架构上使用Adobe Commerce。

>[!NOTE]
>
>随着MariaDB 10.4生命周期结束(EOL)，当前的Adobe Commerce版本将不再支持它。 最佳实践是在任何EOL版本生命周期结束后的30天内停止使用该版本。

## 受影响的产品和版本

* 所有Adobe Commerce本地和云基础架构2.4.4和2.4.5

## 解决方案

采用2024年6月11日发布的新的仅限安全保护的修补程序（2.4.4-p9或2.4.5-p8），以确保与MariaDB 10.5兼容。然后，按照以下步骤从MariaDB 10.4升级到10.5。

### 云部署的升级步骤

1. 使用ECE-Tools DB备份命令[创建](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)数据库备份。 此备份必须在步骤2和3之前完成，以防更新表/行时出现问题。
1. [检查所有压缩表并将其转换为动态表](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/maintenance/mariadb-upgrade)。 此步骤是避免在数据库升级期间潜在的数据丢失所必需的。
1. 检查MYISAM表。 您需要[将所有MyISAM表转换为InnoD](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud)。
1. 准备数据库表和行（前两步）后，使用ECE-Tools DB备份命令创建[DB备份](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)。
1. [打开支持票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)以计划从MariaDB 10.4升级到10.5。在票证中，详细说明您希望数据库升级的日期和时间。 支持团队需要48小时通知，并且商人的开发团队需要可用。 在同意升级的时间和日期后，执行以下操作：
   1. 将您的网站置于维护模式，并停止任何数据库活动，例如crons。
   1. 使用ECE-Tools DB备份命令[创建](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/snapshots)数据库备份。
   1. 让支持人员知道您已通过支持票证完成备份。 要获取查看和跟踪票证的步骤，请参阅我们的支持知识库中的[Adobe Commerce帮助中心用户指南：跟踪您的票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-tickets)。
   1. 然后，Adobe Commerce支持团队开始MariaDB升级过程。 如果已经执行了上述所有步骤，并且数据库为平均大小，那么此过程大约需要一个小时。 较大的数据库需要较长时间。 升级完成后，系统将通过票证通知您。
1. 禁用维护模式。 请参阅我们的开发人员文档中的[启用或禁用维护模式](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。

>[!NOTE]
>
>建议您在每个升级步骤之前和之后创建数据库备份，以消除任何数据丢失的可能性。 如果在版本升级过程中任何时候出现问题，您都可以回滚到上一步。

## 相关阅读

* 本地部署的[数据库升级最佳实践指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/prepare/prerequisites)。
* [在我们的支持知识库中将Adobe Commerce云端上的MariaDB 10.0升级到10.2。](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-0-to-10-2-for-magento-commerce-cloud)
* 在开发人员文档中，[Adobe Commerce生命周期策略](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/lifecycle-policy)。
