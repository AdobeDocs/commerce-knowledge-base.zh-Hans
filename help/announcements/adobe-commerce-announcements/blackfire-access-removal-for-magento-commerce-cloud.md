---
title: 在云基础架构上删除Adobe Commerce的Blackfire访问权限
description: 2020年4月11日，Adobe Commerce on cloud infrastructure Pro计划架构或Adobe Commerce on cloud infrastructure入门计划架构订阅将不再包括免费访问Blackfire性能监控。  您将无法再登录到您的Blackfire帐户。 在4月11日之后，可以直接通过Blackfire.io购买许可证，以继续使用Blackfire。 Adobe Commerce如果到2015年12月14日尚未直接从Blackfire购买许可证，则将停用其免费的Adobe提供Blackfire许可证。 除此之外，将禁用使用Profiler工具创建新报告的功能。 使用托管在云基础架构上的Pro架构的客户仍可以通过New Relic基础架构免费监控基础架构性能。
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# 在云基础架构上删除Adobe Commerce的Blackfire访问权限

2020年4月11日，Adobe Commerce on cloud infrastructure Pro计划架构或Adobe Commerce on cloud infrastructure入门计划架构订阅将不再包括免费访问Blackfire性能监控。  您将无法再登录到您的Blackfire帐户。 在4月11日之后，可以直接通过Blackfire.io购买许可证，以继续使用Blackfire。 Adobe Commerce如果到2015年12月14日尚未直接从Blackfire购买许可证，则将停用其免费的Adobe提供Blackfire许可证。 除此之外，将禁用使用Profiler工具创建新报告的功能。 使用托管在云基础架构上的Pro架构的客户仍可以通过New Relic基础架构免费监控基础架构性能。

**如果要继续使用Blackfire**：

1. 您必须直接通过Blackfire购买许可证。
1. 然后使用这些[步骤](https://blackfire.io/docs/integrations/paas/magentocloud)设置Blackfire。
1. 如果在安装时遇到任何困难，您可以[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以请求帮助。 有关Blackfire的特定问题，请直接通过[support@blackfire.io](mailto:support@blackfire.io)联系Blackfire支持。

## 如果在运行部署时出错：

如果运行部署时出现与Blackfire相关的错误，请执行以下操作：

1. 从配置中删除Blackfire。 编辑`.magento.app.yaml`文件并从运行时节删除Blackfire：

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. 在本地开发环境中完成该操作并将其推送到云。

在运行部署后看到以下错误时，仅[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)：

*PHP警告： PHP启动：无法在未知的行0*&#x200B;中加载动态库“blackfire.so”(已尝试：/usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so：无法打开共享对象文件：没有此类文件或目录)、/usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so：无法打开共享对象文件：没有此类文件或目录)

此错误表示必须更新并停止Blackfire插件加载。

**如果要使用New Relic基础架构**：

要了解如何访问New Relic基础架构，请参阅我们的支持知识库中的[访问New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html)。
