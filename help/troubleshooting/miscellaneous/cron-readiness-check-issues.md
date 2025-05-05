---
title: Cron就绪检查问题
description: '本文为cron就绪问题提供了解决方案。 以下是cron问题的症状：'
exl-id: 1f2cee2c-98ad-4cf5-af16-d736fced2a15
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Cron就绪检查问题

本文为cron就绪问题提供了解决方案。 以下是cron问题的症状：

* 即使设置正确，也会显示有关PHP设置`$HTTP_RAW_POST_DATA`的错误消息。
* PHP就绪检查不会显示PHP版本，如下图所示：
  ![upgr-tshoot-no-cron.png](assets/upgr-tshoot-no-cron.png)
* Commerce管理中会显示以下错误：
  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)
若要查看此错误，可能需要单击窗口顶部的&#x200B;**系统消息**，如下所示：
  ![compman_sys-messages.png](assets/compman_sys-messages.png)

## 检查您现有的crontab {#check-your-existing-crontab}

本节讨论如何查看cron当前是否正在运行，以及验证其设置是否正确。

要验证是否已设置crontab，请执行以下操作：

1. 以[Magento文件系统所有者](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)的身份登录或切换到Commerce服务器。
1. 查看以下文件是否存在： `$ ls -al <magento_root>/var/.setup_cronjob_status`。 如果文件存在，则cron过去已成功运行。 如果文件&#x200B;*不存在*，则表示您尚未安装Adobe Commerce或cron未运行。 无论属于哪种情况，请继续执行下一步。
1. 获取有关cron的更多详细信息。 作为具有`root`权限的用户，输入以下命令： `$ crontab -u <Magento file system owner name> -l`。 例如，在CentOS `$ crontab -u magento_user -l`上。 如果未为用户设置crontab，则会显示以下消息：    `no crontab for magento_user`。 您的crontab将告诉您以下信息：
   * 您正在使用的PHP二进制文件（在某些情况下，您有多个）
   * 您正在运行的Adobe Commerce cron脚本（尤其是这些脚本的路径）
   * cron日志的位置

   请参阅以下部分之一，了解您的问题的解决方案。

## 解决方案：未设置crontab {#solution-crontab-not-set-up}

要验证您的cron作业是否设置正确，请参阅我们的开发人员文档中的[设置cron作业](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/next-steps/configuration)。

## 解决方案：从不正确的PHP二进制文件运行cron {#solution-cron-running-from-incorrect-php-binary}

如果cron作业使用的PHP二进制文件与Web服务器插件不同，则可能会显示PHP设置错误。 要解决此问题，请为PHP命令行和PHP Web服务器插件设置相同的PHP设置。

有关PHP设置的详细信息，请参阅我们的开发人员文档中的[必需的PHP设置](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/php-settings)。

## 解决方案：cron正在运行但出现错误 {#solution-cron-running-with-errors}

尝试手动运行每个命令，因为该命令可能会显示有用的错误消息。 请参阅我们的开发人员文档中的[设置cron作业](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/next-steps/configuration)。

>[!NOTE]
>
>必须运行cron至少&#x200B;*两次*&#x200B;才能执行作业；第一次将作业排入队列，第二次执行作业。
