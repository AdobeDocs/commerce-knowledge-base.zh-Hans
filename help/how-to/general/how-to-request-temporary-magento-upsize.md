---
title: 如何请求云基础架构扩展中的临时Adobe Commerce
description: 如果贵组织正在计划一个在线活动，而您预期该活动将出现高流量，或者您突然发现您的网站正在进行高流量活动，则可以提交[支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)以请求为云基础架构商店上的Adobe Commerce临时添加云容量。
exl-id: 561e2bdd-718a-45c1-8b6c-a0e3a6c8ad04
feature: Cloud, Iaas
source-git-commit: e59335b67e1f33e138e34cab93ce593836d14b48
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# 如何请求云基础架构扩展中的临时Adobe Commerce

如果贵组织正在计划一个您预计会有高流量的在线活动，或者您突然发现您的网站正在进行高流量活动，则可以提交[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，以请求为云基础架构存储上的Adobe Commerce临时添加额外的云容量。

>[!NOTE]
>
>非紧急升级请求需要48小时通知。 升级促销活动不被视为紧急情况，除非站点完全无法正常工作或接收的流量比预期高得多，并且性能严重降低。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## 如何识别高流量事件

在New Relic警报中，您可以使用基线警报条件来定义根据数据行为调整的阈值。

基线警报可用于创建满足以下条件的警报条件：

* 仅在数据行为异常时通知您。
* 动态调整以适应不断变化的数据和趋势，包括每日或每周趋势。

此外，当您还没有已知行为时，基线警报可很好地用于新应用程序。

按照此链接了解有关New Relic [应用智能的异常检测](https://docs.newrelic.com/docs/alerts-applied-intelligence/applied-intelligence/anomaly-detection/anomaly-detection-applied-intelligence/)的更多信息。

如果收到建议高流量事件的警报通知，您可能需要考虑[提交支持票证](/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en#submit-ticket)以请求额外容量。 请按照以下步骤操作。

## 如何监控站点的性能

Adobe为Adobe Commerce on cloud infrastructure提供一套New Relic警报策略专业规划架构和Adobe Commerce on cloud infrastructure入门规划架构用于跟踪以下关键性能指标的生产环境：

* [Apdex得分](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction)
* 错误率
* 磁盘空间（仅适用于Pro体系结构生产环境）

根据行业最佳实践，这些策略可设置影响性能的警告和严重情况的阈值。 当站点遇到触发警报阈值的基础架构或应用程序问题时，New Relic会发送警报通知，以便您能够主动解决该问题。 要使用这些策略，必须配置通知通道以接收警报消息。

按照此链接了解如何[配置基于性能的警报](/docs/commerce-cloud-service/user-guide/monitor/new-relic.html#monitor-performance-with-managed-alerts)。

## 请求临时扩展的步骤

要请求临时性额外云容量，请在Adobe Commerce支持中心提交[支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，并提供以下信息：

>[!NOTE]
>
>*假日临时请求*&#x200B;选项只能在10月到12月之间选择。

1. 选择您需要支持的[!DNL Adobe Commerce]产品：
   * [!DNL Commerce Cloud]
   * [!DNL Commerce on Managed Service]

1. 填写以下字段：
   * **[!UICONTROL Case Title]**
   * **[!UICONTROL Case Description]** *（请确保它们清楚地描述了问题和上下文。）*

1. 从&#x200B;*下拉菜单中选择*&#x200B;基础架构更改请求&#x200B;**[!UICONTROL Issue Reason]**。

1. 从下拉菜单中选择&#x200B;**[!UICONTROL Environment]**。

1. 从下拉菜单中选择相应的&#x200B;**[!UICONTROL Product Version]**。

1. 从&#x200B;*下拉菜单中选择*&#x200B;云项目调整大小(vCPU)**[!UICONTROL Which Infra Change you would like to do today]**。

1. **选择[!UICONTROL Architecture]**：
   * *默认架构：*&#x200B;从&#x200B;*选择大小*&#x200B;下拉菜单中选择&#x200B;**下一个可用大小**。
   * *缩放架构：*&#x200B;选定后，屏幕将更改为显示另外两个字段：
      * Web节点的&#x200B;*大小*
      * *服务节点的大小* *（为每个节点输入所需的大小。）*

1. 以UTC格式（日期和时间）输入&#x200B;**[!UICONTROL From Date]**。

1. 以UTC格式（日期和时间）输入&#x200B;**[!UICONTROL To Date]**。

1. 提供&#x200B;**[!UICONTROL Project URL]** *(可在https://accounts.magento.cloud/下找到，通常采用`https://[REGION].magento.cloud/projects/PROJECT_ID`格式)*

1. 输入&#x200B;**[!UICONTROL Project ID]**。

1. 提供&#x200B;**[!UICONTROL Affected URL]** *（必须以`http://`或`https://`开头。）*

1. 选择&#x200B;**[!UICONTROL Priority]**。

1. 选择&#x200B;**[!UICONTROL Business Impact]**。

1. 确认&#x200B;**[!UICONTROL Time Zone]** *（例如，`(UTC-5:00) Indiana (East)`）*

1. 输入&#x200B;**[!UICONTROL Phone Number]** *（如`+12015550123`）*

1. 单击&#x200B;**[!UICONTROL Submit]**&#x200B;完成您的支持案例。

>[!NOTE]
>
>一旦安排了扩展，自动化系统将调整云实例的大小。 过程完成后，您将不会收到任何票证通知。 您可以使用Adobe Commerce观察工具查看AWS或Azure实例类型，以[验证更改](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)。

## 查看您的升级历史记录

通过向&#x200B;**CSM（客户成功经理）**请求信息，您可以查看所请求调整大小的历史记录。
以下信息适用于每个调整大小请求：

* **大小开始日期**： upsize请求的日期。
* **大小结束日期**：群集返回到先前大小的日期。
* **vCPU大小**：在升级后的群集大小。
* **天使用量**：群集保持升迁的天数。
* **周期vCPU**：将vCPU大小更改为其使用的天数。 （例如，vCPU大小192 x 25天等于4,800）。


## 相关阅读

* 有关如何衡量和改进站点性能的见解、方法和示例，请参阅我们的支持知识库中的以下深入文章：
   * [适用于Adobe Commerce on cloud的CPU分配计算](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
   * [检查云上的Adobe Commerce是否需要针对主机实例进行大小调整](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
   * [检查主机上云中Adobe Commerce的CPU配置](/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* 有关如何识别中断的信息，请参阅我们的支持知识库中的[识别并测量Adobe Commerce在云中的中断](/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)。
* 有关提高站点性能以避免利用容量增加的需求的信息，请参阅我们的开发人员文档中的以下文章：
   * [图像大小](/docs/commerce-admin/catalog/products/digital-assets/product-image-config.html#product-image-resizing)
   * [全页缓存](/docs/commerce-admin/systems/tools/cache-management.html#full-page-caching)
   * [ECE-Tools](/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)
