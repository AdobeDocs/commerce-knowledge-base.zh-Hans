---
title: cron疑难解答
description: 本文提供了针对Adobe Commerce本地产品中cron问题的故障排除解决方案。
exl-id: e69a4fb3-731b-449e-a815-c33cd2faa567
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# cron疑难解答

本文提供了针对Adobe Commerce本地产品中cron问题的故障排除解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署2.2.x、2.3.x
* Magento Open Source2.2.x和2.3.x

## 问题

## 以下是cron问题的症状：

* 您的更新或升级从不运行；它保持在`pending`状态。
* 即使设置正确，也会显示有关PHP设置`$HTTP_RAW_POST_DATA`的错误消息。
* cron就绪检查失败。 可能的错误包括不可写路径和未设置cron。 下面是一个示例：

  ![upgr-tshoot-no-cron2.png](assets/upgr-tshoot-no-cron2.png)

* PHP准备情况检查不会显示PHP版本，如下图所示。

  ![Screen_Shot_2019-08-29_at_1.36.08_PM.png](assets/Screen_Shot_2019-08-29_at_1.36.08_PM.png)

* Commerce管理中会显示以下错误：

  ![compman-cron-not-running.png](assets/compman-cron-not-running.png)

若要查看此错误，可能需要单击窗口顶部的&#x200B;**系统消息**，如下所示：

![compman_sys-messages.png](assets/compman_sys-messages.png)

## 调查以找出原因 {#check-your-existing-crontab}

本节讨论如何查看cron当前是否正在运行，以及验证其设置是否正确。

要验证是否已设置crontab，请执行以下步骤：

1. 以[Magento文件Magento所有者](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/file-system/overview)的身份登录或切换到您的系统服务器。
1. 查看以下文件是否存在：    `bash    ls -al <magento_root>/var/.setup_cronjob_status`。 如果文件存在，则cron过去已成功运行。 如果文件&#x200B;*不存在*，则表示您尚未安装Magento或cron未运行。 无论属于哪种情况，请继续执行下一步。
1. 获取有关cron的更多详细信息。 作为具有`root`权限的用户，输入以下命令：    `bash    crontab -u <Magento file system owner name> -l`。 例如，在CentOS `bash    crontab -u magento_user -l`上。  如果未为用户设置crontab，则会显示以下消息：    `terminal    no crontab for magento_user`。 您的crontab将告诉您以下信息：

   * 您正在使用的PHP二进制文件（在某些情况下，您有多个）
   * 您正在运行哪些Magentocron脚本（特别是这些脚本的路径）
   * cron日志的位置

请参阅以下部分之一，了解您的问题的解决方案。

## 解决方案

### 未设置crontab的解决方案 {#solution-crontab-not-set-up}

要验证您的cron作业是否设置正确，请参阅[设置cron作业](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration)。

### 从不正确的PHP二进制文件运行的cron的解决方案 {#solution-cron-running-from-incorrect-php-binary}

如果cron作业使用的PHP二进制文件与Web服务器插件不同，则可能会显示PHP设置错误。 要解决此问题，请为PHP命令行和PHP Web服务器插件设置相同的PHP设置。

有关PHP设置的详细信息，请参阅我们的开发人员文档中的[必需的PHP设置](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings)。

### cron运行有错误的解决方案 {#solution-cron-running-with-errors}

尝试手动运行每个命令，因为该命令可能会显示有用的错误消息。 查看[设置cron作业](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/next-steps/configuration)。

>[!NOTE]
>
>必须运行cron至少&#x200B;*两次*&#x200B;才能执行作业；第一次将作业排入队列，第二次执行作业。
