---
title: 如何检查 [!DNL cron] 被禁用的原因
description: 本文为云基础架构产品上的Adobe Commerce中的cron问题提供了故障排除解决方案。
feature: Configuration
role: Developer
exl-id: d4d4a28d-3afa-4379-afc1-bc6250717784
source-git-commit: c5e94c6407394cd905ea470628d28db2c2c6c0ed
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# 如何检查禁用[!DNL cron]的原因

本文为云基础架构产品上的Adobe Commerce中的[!DNL cron]问题提供了故障排除解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有版本

## 问题

## 以下是[!DNL cron]问题的症状：

您注意到您的[!DNL cron]未运行。
例如：您在`app/etc/env.php`文件中看到以下行：

```'cron' =>
  array (
    'enabled' => 0
  ),
```

空数组表示[!DNL cron]已启用&#x200B;**&#x200B;**：

```'cron' =>
  array (
  ),
```

## 原因

[!DNL cron]当前处于非活动状态的原因有多种：

1. 由于缺少[!DNL OpCache]设置，[!DNL cron]已禁用。
1. 基础架构团队禁用了您的[!DNL cron]，因为它导致您的站点性能不佳/不可用。
1. 未重新启用[!DNL cron]，因为您的部署失败。

请参阅以下部分之一，了解您的问题的解决方案。

## 解决方案

### 针对缺少[!DNL OpCache]设置的解决方案 {#solution-missed-opcache-settings}

查看Commerce知识库中由于配置错误或缺少 [!DNL OpCache] 设置[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/crons-blocked-running-missing-opache-settings)而停止的[!DNL Cron] 。

### 基础架构团队禁用的解决方案 {#solution-disabled-by-infrastructure-team}

1. 检查您以前的支持工单，其中您的站点已关闭或未响应。
1. 然后，检查基础架构团队是否表明他们已禁用该功能。
1. 确认您已解决基础架构团队提出的问题/顾虑。
1. 如果您需要进一步的帮助来请求重新启用[!DNL cron]，请提交[支持请求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets)，并解释您如何解决了基础架构团队指出的问题。

### 部署解决方案失败 {#solution-deployment-failed}

检查部署日志：

* 在我们的Commerce on Cloud Infrastructure指南中[查看和管理日志](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations)。
* [正在检查部署日志，如果Cloud UI在Commerce知识库中存在&#x200B;*`log snipped`*&#x200B;错误](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/checking-deployment-log-if-the-cloud-ui-shows-log-snipped-error)。

1. 如果部署在`setup:upgrade`步骤中失败，则不会重新启用[!DNL cron]。
例如：您会在部署日志中看到以下行：

   ```The command "/bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade --keep-generated --ansi --no-interaction  | tee -a /app/$<project_id>/var/log/install_upgrade.log"" failed. Cache types config flushed successfully```

1. 否则，部署可能在其他某个阶段失败。 检查部署日志，并确保这两行都显示（如下示例）。 如果您在日志中未看到与此类似的两行，则表示[!DNL cron]未重新启用：

   ```  [2024-03-06T10:55:39.345564+00:00] INFO: Disable cron```<br>
...<br>
   ```  [2024-02-07T10:50:09.579005+00:00] INFO: Enable cron```

如果需要进一步的帮助，**提交[支持请求](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-tickets)。**
