---
title: 导出的产品.csv文件不显示
description: 本文修复了以下问题：您尝试在Commerce管理员中将所需的实体类型导出到.csv文件，但文件未显示。
exl-id: 8e3bb65c-ea75-4af4-ad4b-4d94ab219bbb
feature: Cache, Data Import/Export, Products, Variables
role: Developer
source-git-commit: b6f1222918b027eaecda42b767e6f83b2cf0f5d0
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# 导出的产品.csv文件不显示

本文为在Commerce管理员中将所需的实体类型导出到.csv文件导致不显示该文件的问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)。

## 问题

<u>重现步骤</u>

先决条件： **将密钥添加到URL**&#x200B;选项设置为&#x200B;*是*。 该选项已在Commerce管理员的&#x200B;**商店** > **配置** > **高级** > **管理员** > **安全性**&#x200B;下配置。

1. 在管理员中，导航到&#x200B;**系统** > **数据传输** > **导出**。

   ![magento_export_products_2.3.4.png](assets/magento_export_products_2.3.4.png)

1. 选择
   * **实体类型**：要导出的实体
   * **导出文件格式**： *CSV*
   * **字段存储模块**：保持未选中状态。
1. 单击&#x200B;**继续**。
1. 显示以下消息： *“消息已添加到队列，请等待以尽快获取文件”*。

<u>预期的结果</u>

包含导出的所需实体类型的.csv文件会在几分钟内显示在网格中。

<u>实际结果</u>

包含导出的所需实体类型的.csv文件在10分钟或更长时间后不会显示在网格中。

## 原因

Adobe Commerce应用程序部件版本2.3.2中的导出功能存在的已知问题。

## 解决方案

对于此问题，有两种可能的解决方案：

* 禁用“将密钥添加到URL”选项。
* 手动运行`bin/magento queue:consumers:start exportProcessor`命令，并可以选择将其配置为由cron运行。

请参阅以下段落中有关这两个选项的详细信息。

### 禁用“将密钥添加到URL”选项

1. 在管理员中，导航到&#x200B;**商店** > **配置** > **高级** > **管理员** > **安全性**。
1. 将&#x200B;**将密钥添加到URL**&#x200B;选项设置为&#x200B;*否*
1. 单击&#x200B;**保存配置**。
1. 清理&#x200B;**系统** > **工具** > **缓存管理**&#x200B;下的缓存，或者通过运行    ```bash    bin/magento cache:clean```或管理员中的。

### 手动运行导出命令，并可选择将其添加为cron作业

要获取导出文件，请运行`bin/magento queue:consumers:start exportProcessor`命令。 运行此操作后，文件应显示在网格中。


要选择性地将进程添加为cron作业，您必须将`CRON_CONSUMERS`变量添加到`.magento.env.yaml`文件。

#### 将进程添加为cron作业（可选）

1. 确保已设置和配置您的cron。 有关详细信息，请参阅[设置cron作业](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html)。
1. 运行以下命令以返回消息队列使用者的列表：     `./bin/magento queue:consumers:list`
1. 将以下内容添加到根应用程序目录中的`.magento.env.yaml`文件，并包含要添加的使用者。 例如，以下是导出处理所需的使用者：

   ```yaml
   stage:
       deploy:
           CRON_CONSUMERS_RUNNER:
               cron_run: true
               max_messages: 1000
               consumers:
                   - exportProcessor
   ```

   然后，推送此更新文件并重新部署您的环境。 在开发人员文档中还引用[将自定义cron作业添加到您的项目](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#add-custom-cron-jobs-to-your-project)。

>[!NOTE]
>
>如果您找不到环境的`.magento.env.yaml`文件，并且认为该文件已被删除，则需要创建一个新的`.magento.env.yaml`。 最初可能为空，您可以根据需要在该处添加信息。 引用以下文章：开发人员文档中的[为部署](/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html)配置环境变量[以及环境变量](/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html)。

>[!TIP]
>
>[YAML文件](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html?lang=zh-Hans)区分大小写，不允许制表符。 请注意在整个.magento.env.yaml文件中使用一致的缩进，否则您的配置可能无法按预期工作。 文档和示例文件中的示例使用双空格缩进。 使用ece-tools validate命令检查配置。

>[!NOTE]
>
>在Adobe Commerce on cloud infrastructure Pro项目中，必须在云基础架构上的Adobe Commerce上启用[自动cron功能](/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=en#crontab)，然后才能使用`.magento.app.yaml`将自定义cron作业添加到暂存和生产环境。 如果未启用此功能，请[创建支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以便为您添加作业。
