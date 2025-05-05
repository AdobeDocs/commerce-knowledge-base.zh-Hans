---
title: 针对PHP漏洞的Adobe Commerce Recommendations
description: 9月3日，多状态信息共享和分析中心(MS-ISAC)发布了与多个漏洞相关的警报，这些漏洞可能允许执行任意代码，并建议所有使用PHP的站点尽快更新到最新的PHP版本（此处提供了完整的警报）(https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)。
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# 针对PHP漏洞的Adobe Commerce Recommendations

9月3日，多状态信息共享和分析中心(MS-ISAC)发布了与多个漏洞相关的警报，这些漏洞可能允许执行任意代码，并建议所有使用PHP的站点尽快更新到最新的PHP版本（[此处提供了完整警报](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)）。

>[!WARNING]
>
>关于Adobe Commerce on cloud infrastructure，请注意，如果没有48个工作小时的通知，就无法将服务升级推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。 因此，在更改需要投入生产前48小时[提交支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，其中详细列出所需的服务升级并指明希望升级过程开始的时间。

请阅读并了解Adobe Commerce网站的影响和步骤：

在我们的云产品上托管&#x200B;**Adobe Commerce**

如果您在云基础架构上使用Adobe Commerce，请与您的技术团队合作，随时开始重新部署Adobe Commerce\*以便利用更新。 我们建议商家在9月30日之前完成此重新部署，以避免由于本月末的这些漏洞而可能生效的PCI合规性问题。

有关为此更新重新部署云站点的其他说明：

* 如果您的站点仍在使用PHP版本7.0，则需要在重新部署之前先升级到支持的PHP版本，以便利用这些安全更新。
* 对于2.1.x/2.2.x，有关升级PHP的更多信息可在[此处](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=zh-Hans)找到。

\* *本文和我们的消息传递的先前版本显示为9月19日，但我们的团队已提前完成工作。*

所有其他托管解决方案上的&#x200B;**Adobe Commerce**

由于Adobe Commerce依赖于PHP，我们建议所有使用Adobe Commerce的商家与其托管提供商一起审查PHP的必要更新。 我们还建议商家在9月30日之前完成此审查以及任何更新，以避免由于本月末的这些漏洞而可能生效的PCI合规性问题。

请注意Adobe Commerce关于其他托管解决方案的一些其他详细信息：

* 使用7.1之前或更高版本的PHP的Adobe Commerce版本2.0或1.x没有可用的PHP官方补丁。 建议的路径是将PHP升级到支持的PHP版本。

根据警报，建议对此漏洞使用的修补程序包括：

* PHP 7.1： [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2： [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3： [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

如果您想了解有关PHP和最新版本的更多信息，请访问[PHP的站点](https://www.php.net/)。 如果您有任何问题或想了解有关安全最佳实践的更多信息，请查看我们的[安全最佳实践指南](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf)。
