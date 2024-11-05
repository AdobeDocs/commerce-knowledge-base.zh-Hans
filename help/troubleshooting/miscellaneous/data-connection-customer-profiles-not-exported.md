---
title: 客户配置文件未出现在Experience Platform中
description: 如果使用 [!DNL Data Connection] 扩展时，Experience Platform中未显示您的客户配置文件数据，本文将提供故障排除步骤。
feature: Personalization, Integration, Configuration
role: Admin, Developer
exl-id: 4f12b032-0bee-47da-927a-8d4c2d8b8276
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# 客户配置文件未出现在Experience Platform中

如果使用Data Connection扩展时，Experience Platform中未显示您的客户配置文件数据，本文提供故障排除步骤。

## 受影响的产品和版本

* 已安装Adobe Commerce 2.4.x和[!DNL Data Connection]扩展

## 问题

您已安装和配置[[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview)扩展并启用将客户配置文件数据发送到Experience Platform的功能，但该配置文件数据未出现在Experience Platform中。

## 解决方案

如果Experience Platform中未显示客户配置文件信息，请检查以下各项：

### 确认已安装最新版本的[!DNL Data Connection]

确保您已安装最新版本的`experience-platform-connector`扩展。

有关最新版本的信息，请参阅[[!DNL Data Connection] 扩展发行说明](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/release-notes)。

>[!NOTE]
>
>[!DNL Data Connection]扩展的最新版本包括`customers-connector`模块，该模块负责向Experience Platform发送配置文件数据。 `customers-connector`模块应为版本`1.2.0`或更高版本。

### 确认已配置客户连接器模块

确认已根据您的安装方案配置了`customers-connector`模块。

#### 云基础架构上的Adobe Commerce

1. 在`.magento.env.yaml`中启用`ENABLE_EVENTING`全局变量。 [了解更多](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global)。

   ```bash
       stage:
           global:
               ENABLE_EVENTING: true
   ```

1. 提交更新的文件并将其推送到云环境。 部署完成后，使用以下命令启用发送事件：

   ```bash
       bin/magento config:set adobe_io_events/eventing/enabled 1
   ```

#### Adobe Commerce内部部署

执行以下命令以启用代码生成和Adobe Commerce事件：

```bash
   bin/magento events:generate:module
   bin/magento module:enable Magento_AdobeCommerceEvents
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   bin/magento config:set adobe_io_events/eventing/enabled 1
```

### 确认您已启用要捕获并发送到Experience Platform的配置文件数据

在Commerce管理员中，确保设置了以下字段：

* 在&#x200B;**[!UICONTROL System]** > **[!UICONTROL Services]** > **[!UICONTROL Data Connection]**&#x200B;中，验证[!UICONTROL Back office events]和[!UICONTROL Customer profiles]复选框是否已启用。
* 确保&#x200B;*[!UICONTROL Profile Dataset ID]*&#x200B;字段正确，并且与您当前用于行为和后台事件数据的数据集不同。

### 检查事件是传送到暂存还是生产

1. 运行以下命令以显示当前Adobe Developer环境：

   ```bash
   Copy code
   bin/magento config:show
   adobe_io_events/integration/adobe_io_environment
   ```

1. 如果环境设置为&#x200B;*[!UICONTROL Stage]*，请使用以下命令将其更改为&#x200B;*[!UICONTROL Production]*：

   ```bash
   Copy code
   bin/magento config:set adobe_io_events/integration/adobe_io_environment
   production
   ```

### 查询事件数据SaaS表

连接并执行以下[!DNL SQL]查询，以验证
`event_data_saas`表并且没有错误：

```sql
Copy code
select * from event_data_saas;
```

### 处理事件发布错误

1. 如果遇到以下错误，请确保沙盒和生产SaaS连接器密钥正确：

   ```css
   Copy code
   2024-06-07 14:37:57 | 2024-06-07 14:38:03 | 1 | 0 | Event publishing
   failed: Error code: 403; reason: Forbidden { "error": { "code":
   "Forbidden", "message": "Client ID is invalid", "details": {
   "error_code": "403003" } } }
   ```

1. 转到管理员中的&#x200B;*[!UICONTROL Commerce Services Connector]*&#x200B;页面，并确保指定的[!UICONTROL sandbox/production]密钥已正确配置。 此外，请确认Commerce帐户[!UICONTROL sandbox/production]设置与[!UICONTROL Commerce Services Connector]中显示的设置匹配。 了解[更多](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas#apikey)。

### 检查服务ID是否在允许列表中，并与Adobe Commerce支持部门确认

1. 列入允许列表验证[!UICONTROL Commerce Services Connector] `serviceId`是否显示在Adobe Commerce的中。
1. 联系[Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)以确认允许列表状态。

## 相关阅读

* Commerce Services用户指南中的[[!DNL Data Connection]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview)扩展
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
