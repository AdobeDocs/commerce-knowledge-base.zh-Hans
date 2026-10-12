---
title: 检查部署日志，如果Cloud UI出现“日志截断”错误
description: 本文为以下问题提供了解决方案：云基础架构上的Adobe Commerce在尝试在云项目UI上查看部署日志时，显示*日志片段，因为它太长*错误消息。
exl-id: 04d28741-72c1-4722-be46-425fe136b9a6
feature: Cloud, Deploy, Logs, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%
---
# 正在检查Cloud UI是否具有&#x200B;*日志片段*&#x200B;错误

本文针对以下问题提供了解决方案：在云项目UI上尝试查看部署日志时，云基础架构UI上的Adobe Commerce显示&#x200B;*日志片段，因为该片段太长*&#x200B;错误消息。 （不适用于[Adobe Commerce云控制台](https://console.adobecommerce.com/)。）

## 受影响的产品

云基础架构上的Adobe Commerce（所有受支持的版本）

## 问题

尝试在云项目UI上查看部署日志时，云基础架构UI上的Adobe Commerce显示以下错误消息： *日志片段，因为它太长*。

## 重现问题的步骤

1. 转到项目URL，然后单击相关部署的&#x200B;**状态**。
1. 如果日志太长无法在UI中显示，则会显示错误消息： *日志已截断，因为日志太长*。

## 原因

请注意，不应将UI中显示的日志视为事实来源，尤其是当您在以“成功”状态列出部署后发现站点未响应或无法正常工作时。 您还应使用服务器上的日志进行验证。 请参阅我们的开发人员文档中的[查看和管理日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hans)。

## 解决方案

1. 确保已在本地环境中安装[Magento Cloud CLI](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli.html?lang=zh-Hans)。
1. 可以运行以下任一命令：

   ```bash
   magento-cloud act -p <project id> -e <environment>
   ```

   ```bash
   magento-cloud activity:list -p <project id> -e <environment>
   ```

1. 它们将返回类似于以下内容的输出：

   ```bash
   Activities on the project <project name> (project id), environment <environment>:
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | ID            | Created                   | Description                         | Progress | State    | Result  |
   +---------------+---------------------------+-------------------------------------+----------+----------+---------+
   | l5wgwmzwrsskg | 2021-06-01T08:18:02-07:00 | ABC merged Integration into Staging | 100%     | complete | success |
   | raah5xrhqz3wg | 2021-06-01T08:07:18-07:00 | XYZ pushed to Integration           | 100%     | complete | failure |
   ```

1. 复制受影响部署的活动ID，然后运行命令：

   ```bash
   magento-cloud activity:log <activity ID> -p <project id> -e <environment>
   ```

   检查失败部署的日志的示例：

   ```bash
   magento-cloud activity:log raah5xrhqz3wg -p <project id> -e <environment>
   ```

## 我们的开发人员文档中的相关阅读：

* [云基础架构上的Adobe Commerce >构建和部署](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=zh-Hans)
* [云基础架构上的Adobe Commerce >查看和管理日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=zh-Hans)
