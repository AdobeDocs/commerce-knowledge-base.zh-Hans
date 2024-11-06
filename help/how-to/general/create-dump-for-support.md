---
title: 如何在支持代理请求时创建“已清理”转储
description: 当Adobe Commerce支持代理请求提供数据库转储（备份）时，本文介绍了如何从Adobe Commerce管理员创建“已清理”数据库转储（备份）和代码。 此转储不包括您的媒体文件，以加快处理过程并生成更小的文件。 在进行数据库备份时，所有敏感数据都将进行哈希处理。
exl-id: ad088bd2-3f92-416e-89f0-d037d53cd6a9
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 如何在支持代理请求时创建“已清理”转储


## 受影响的产品和版本

Adobe Commerce（所有部署方法）2.3.x、2.4.x。

## 创建“已清理”的转储

从管理员创建一个“已清理”转储：

1. 在Commerce管理员中，转到&#x200B;**系统** > **支持** > **数据收集器**。
1. 单击&#x200B;**新建备份**。
1. 几分钟后，单击&#x200B;**刷新状态** （可能需要更长时间，每5分钟重复一次直到完成）。
1. 将生成的转储文件从`/var/support`目录重定位到Adobe Commerce根目录。

然后，您可以向支持人员提供转储文件的直接下载链接（您的商店地址和所显示的文件名）。

如果从管理员创建转储时遇到问题，请考虑使用CLI命令，如开发人员文档中的[运行支持实用工具](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/run-support-utilities)中所述。

## 相关阅读

* [在我们的支持知识库中为Adobe Commerce在云基础架构上创建完整数据库备份](/help/how-to/general/create-database-dump-on-cloud.md)。
