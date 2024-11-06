---
title: Adobe Commerce在云基础架构上的第三方测试提示
description: 当您在云基础架构上使用Adobe Commerce的扩展遇到问题时，本文提供了与第三方共享访问权限以进行测试/验证的选项。
exl-id: e2d80aa9-8b68-48ed-bec5-68e128611a1e
feature: Best Practices, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Adobe Commerce在云基础架构上的第三方测试提示

当您在云基础架构上使用Adobe Commerce的扩展遇到问题时，本文提供了与第三方共享访问权限以进行测试/验证的选项。
在决定向第三方提供访问的方式时，您应遵循适当的内部数据安全程序和要求。

## 受影响的产品和版本：

* 云基础架构上的Adobe Commerce 2.3.0 - 2.3.7-p1， 2.4.0 - 2.4.3

## 使用哪些环境进行测试

根据您的内部安全标准，您可以选择在本地环境中进行第三方故障排除。 如果无法在本地重现问题，您可能希望提供对云环境的访问权限。 如果您选择这样做，请确保遵循您的内部安全标准。 如果提供对任何云环境的访问权限，请确保您的第三方清楚知道可以执行的操作，以及仅复制或允许代码更改等操作需要什么批准。 这对于生产环境尤其重要。

## 为第三方提供访问和数据

* 为第三方供应商提供对云环境的访问权限。 相关文章：

   * [Adobe Commerce帮助中心用户指南>共享访问权限：授予其他用户访问您帐户的权限](/help/help-center-guide/help-center/magento-help-center-user-guide.md#shared-access)（位于我们的支持知识库中）。
   * 在我们的用户指南中[共享您的Commerce帐户](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-share)。

* 创建数据库转储（或授予第三方供应商执行此操作的权限）。 可以使用CLI或Commerce Admin执行此操作。 此数据库转储将混淆客户数据，因此他们获得的只是代码和产品SKU等，没有专有/客户数据。 请参考我们的支持知识库中的[共享您的Commerce帐户] (/help/how-to/general/create-database-dump-on-cloud.md)。
* 测试完成后，请确保按照支持知识库中的[Adobe Commerce帮助中心用户指南>撤消（删除共享访问权限）](/help/help-center-guide/help-center/magento-help-center-user-guide.md#revoke-shared-access)中所述，撤消对云环境的共享访问权限。

## 测试最佳实践

标准做法是对本地环境进行故障排除。 如果无法本地重现问题，请转到“暂存”。 第三方可能需要检查生产。 确保您的第三方知道，他们仅尝试在生产环境和暂存环境中重现问题，不会进行任何代码更改，如果他们需要更改代码，则必须先获得您的权限。

## 相关阅读

* 在我们的支持知识库中[在Adobe Commerce中使用第三方扩展的最佳实践](https://support.magento.com/hc/en-us/articles/360042361152-Best-Practices-for-using-third-party-extensions-in-Magento)。
