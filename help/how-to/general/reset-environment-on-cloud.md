---
title: 在云基础架构上重置Adobe Commerce上的环境
description: 本文显示了在Adobe Commerce上回滚云基础架构上环境的各种方案。
exl-id: e6b27838-ca1e-415f-a098-2aa2576e3f20
feature: Best Practices, Build, Cloud, Console
source-git-commit: 4327f464fb8eebf30a380e9e58afe55c3e613e52
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# 在云基础架构上重置Adobe Commerce上的环境

本文显示了在Adobe Commerce上回滚云基础架构上环境的各种方案。
>[!NOTE]
>
>本指南适用于所有Cloud Starter环境，并且仅适用于Cloud Pro上的集成环境。

选择最适合您的具体情况：

* 如果您有计划的活动（计划的部署或升级） — [方案1：计划的活动)](#scen1)。
* 如果您具有有效的快照 — [方案2：还原快照](#scen2)。
* 如果您具有稳定的生成，但没有有效的快照 — [场景3：没有快照，则生成稳定（SSH连接可用）](#scen3)。
* 如果生成已损坏，并且您没有有效的快照 — [方案4：没有快照；生成已损坏（无SSH连接）](#scen4)。

## 场景1：计划活动

在计划的部署或升级中，最简单且建议使用的[!UICONTROL Rollback]是让商家在准备过程中执行以下操作：

>[!NOTE]
>
>始终首先在较低级别的环境中测试这些步骤！

<u>升级/部署活动前5天</u>：

1. 检查当前数据库的大小。
1. 检查`/data/exports`上是否有足够的磁盘空间来容纳[!UICONTROL Database Dump]。 如果磁盘空间不足，请删除不需要的数据，或者创建支持案例并请求扩展磁盘。

<u>更改日期</u>：

1. 将网站放入[!UICONTROL Maintenance Mode]。
详细了解用户指南中的[启用或禁用[!UICONTROL Maintenance Mode]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/maintenance-mode.html?lang=zh-Hans)，以及升级指南中的升级[&#128279;](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html?lang=zh-Hans)的[!UICONTROL Maintenance Mode]选项。
1. 禁用cron作业。 有关禁用cron作业的详细信息，请参阅[crons属性指南](<https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property#disable-cron-jobs>)。
1. 获取本地[[!UICONTROL Database Dump]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/create-database-dump-on-cloud.html?lang=zh-Hans)。

<u>如果需要[!UICONTROL Rollback]</u>：

1. 如果应用程序（如[!DNL MariaDB]）已作为此计划活动的一部分升级，请首先将该应用程序重新安装到以前的版本。
1. [!UICONTROL Rollback]使用本地[!UICONTROL Database Dump]的数据库，并将其导入回[!DNL MariaDB]。
1. 通过[!DNL Git]将代码[!UICONTROL Rollback]到以前的工作版本。

对于升级/计划活动[!UICONTROL rollbacks/restores]，建议不要使用[!UICONTROL Snapshots]，因为与本地[!UICONTROL Database Dump]相比，检索数据需要更长的时间，如上面&#x200B;**步骤2中所示，如果需要[!UICONTROL Rollback]**&#x200B;部分。

[!UICONTROL Snapshots]不保存在节点/服务器上，而是保存在单独的存储块中，由于该数据必须通过网络从块存储传输到新磁盘，因此该过程需要时间。 然后，将该新磁盘装载到节点上，准备检索/导入到连接到节点/服务器的原始磁盘上。

将此与导入本地[!UICONTROL Database Dump]进行比较时，节点/服务器上已可检索数据，因此会节省大量时间，因为只需要使用[!UICONTROL Database Import]。

## 场景2：恢复快照

阅读：我们的开发人员文档中的[在Adobe Commerce上还原云基础架构上的快照](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#restore-snapshot)。

>[!NOTE]
>
>在访问云基础架构帐户上的Adobe Commerce之后以及在应用重大更改之前，创建快照必须是我们的第一步。 这是最佳实践，强烈推荐。

阅读：在我们的开发人员文档中创建[快照](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/storage/snapshots#create-snapshot)。

## 场景3：无快照，构建稳定（可用SSH连接）

此部分说明如何在尚未创建快照但可以通过SSH访问环境时重置环境。

步骤如下：

1. 禁用配置管理。
1. 卸载Adobe Commerce软件。
1. 重置[!DNL git]分支。

执行这些步骤后：

* Adobe Commerce安装将返回到其Vanilla状态（数据库已恢复；部署配置已删除；已清除`var`下的目录）。
* 您的[!DNL git]分支在过去将被重置为所需的状态。

请阅读下面的详细步骤。

### 步骤0（先决条件）：删除config.php以禁用配置管理

我们需要禁用配置管理，以便它不会在部署期间自动应用以前的配置设置。

要禁用配置管理，请确保您的`/app/etc/`目录不包含`config.php`文件。

要删除配置文件，请执行以下步骤：

1. [SSH到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans)。
1. 删除配置文件： `rm app/etc/config.php`

阅读有关配置管理的更多信息：

* [在我们支持知识库中，减少Adobe Commerce在云基础架构上的部署停机时间](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)。
* 在开发人员文档中[商店设置的配置管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=zh-Hans)。

### 步骤1：使用setup：uninstall命令卸载Adobe Commerce软件


卸载Adobe Commerce软件将删除并还原数据库，删除部署配置，并清除`var`下的目录。

阅读：在开发人员文档中[卸载Adobe Commerce软件](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall.html?lang=zh-Hans)。

要卸载Adobe Commerce软件，请执行以下步骤：

1. [SSH到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans)。
1. 执行`setup:uninstall`： `bin/magento setup:uninstall`
1. 确认卸载。

将显示以下消息以确认卸载成功：

```php
[SUCCESS]: Magento uninstallation complete.
```

这意味着我们已将Adobe Commerce安装（包括DB）恢复到其正版(Vanilla)状态。

### 步骤2：重置[!DNL git]分支

通过[!DNL git]重置，我们将代码还原到过去所需的状态。

1. 将环境克隆到本地开发环境。 您可以在Cloud Console中复制命令：    ![copy_git_clone.png](assets/copy_git_clone.png)
1. 访问提交历史记录。 使用`--reverse`以相反顺序显示历史记录，以便更加方便： `git log --reverse`
1. 选择已完成的提交哈希。 要将代码重置为其真实状态(Vanilla)，请查找创建分支（环境）的第一次提交。
   ![替换文本](image.png)
1. 应用硬[!DNL git]重置： `git reset --h <commit_hash>`
1. 将更改推送到服务器： `git push --force <origin> <branch>`

执行这些步骤后，将重置[!DNL git]分支并清除整个[!DNL git]更改日志。 最后[!DNL git]个推送将触发重新部署，以应用所有更改并重新安装Adobe Commerce。

## 场景4：没有快照；生成已中断（没有[!DNL SSH]连接）

本节说明如何在环境处于关键状态时重置环境：部署过程无法成功构建工作应用程序，从而导致[!DNL SSH]连接不可用。

在这种情况下，必须首先使用[!DNL git]重置来恢复Adobe Commerce应用程序的工作状态，然后卸载Adobe Commerce软件（要删除并恢复数据库，删除部署配置等）。 该场景包含与场景3相同的步骤，但步骤顺序不同，并且还有一个额外的步骤 — 强制重新部署。 步骤如下：

1. [重置 [!DNL git] 分支。](/help/how-to/general/reset-environment-on-cloud.md#reset-git-branch)
1. [禁用配置管理。](/help/how-to/general/reset-environment-on-cloud.md#disable_config_management)
1. [卸载Adobe Commerce软件。](/help/how-to/general/reset-environment-on-cloud.md#setup-uninstall)
1. 强制重新部署。

执行这些步骤后，您的结果将与场景3中的结果相同。

### 步骤4：强制重新部署

进行提交（这可能是空提交，但我们不建议这样做）并将它推送到服务器以触发重新部署：

```git
git commit --allow-empty -m "<message>" && git push <origin> <branch>
```

## 如果安装：卸载失败，请手动重置数据库

如果执行`setup:uninstall`命令失败并出现错误，且无法完成，则可以使用以下步骤手动清除数据库：

1. [SSH到您的环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans)。
1. 连接到MySQL数据库： `mysql -h database.internal` （对于Pro环境，请参阅： [设置MySQL服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html?lang=zh-Hans)）。
1. 删除`main`数据库： `drop database main;`
1. 创建空的`main`数据库： `create database main;`
1. 删除以下配置文件： `config.php`、`config.php.bak`、`env.php`、`env.php.bak`

重置数据库后，[向环境推送 [!DNL git] 以触发重新部署](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli.html?lang=zh-Hans)并将Adobe Commerce安装到新创建的数据库中。 或[运行重新部署命令](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=zh-Hans#environment-commands)。
