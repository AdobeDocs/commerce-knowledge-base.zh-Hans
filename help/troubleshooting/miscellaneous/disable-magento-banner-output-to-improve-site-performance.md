---
title: 禁用Adobe Commerce横幅输出以提高网站性能
description: 本文修复了站点性能较低的问题。 启用但未使用“Magento_Banner”模块可能会导致网站性能降低。 禁用模块输出可以提高站点性能。 查看文章以了解解决步骤。
exl-id: 90a8bd21-1f2c-4cfe-8213-17f877e20de8
feature: Configuration
role: Developer
source-git-commit: 76ef59dc37504f50d55734a90c9ce5b30bb83175
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# 禁用Adobe Commerce横幅输出以提高网站性能

本文修复了站点性能较低的问题。 网站性能不佳可能是由启用了`Magento_Banner`模块但未使用造成的。 禁用模块输出可以提高站点性能。 查看文章以了解解决步骤。

>[!NOTE]
>
>如果您使用Adobe Commerce Banner功能，请参阅我们的支持知识库中的[高吞吐量AJAX请求导致性能降低](/help/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.md)文章，以获取有关如何避免过多Ajax请求导致的性能问题的建议。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce v.2.x.x
* Adobe Commerce内部部署v.2.2.x和2.3.x

## 问题

`Magento_Banner`模块已启用，但未使用。

要检查是否出现这种情况，请执行以下操作：

对于Adobe Commerce on cloud infrastructure 2.2.x：

1. 登录到Commerce管理员。
1. 导航到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Banners]**。
1. 如果此页面上显示的网格为空，则表示您没有任何横幅。

如果在&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]**&#x200B;下未看到&#x200B;**[!UICONTROL Banners]**&#x200B;选项，则表示您已应用本文中的推荐。

对于Adobe Commerce on cloud infrastructure 2.3.x及更高版本（在v 2.3.x](https://commerce-docs.github.io/devdocs-archive/2.3/guides/v2.3/release-notes/ReleaseNotes2.3.0Commerce.html#banner-now-dynamic-block)中功能[已重命名）：

1. 登录到Commerce管理员。
1. 导航到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Dynamic Blocks]**。
1. 如果此页面上显示的网格为空，则表示您没有任何动态块（横幅）。

如果在&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]**&#x200B;下未看到&#x200B;**[!UICONTROL Dynamic Blocks]**&#x200B;选项，则表示您已应用本文中的推荐。 若要再次查看横幅选项，请反转此过程。

## 原因

启用`Magento_Banner`模块后，Adobe Commerce会将Ajax请求从店面发送到服务器以获取横幅信息。 这些Ajax请求会对性能产生影响，尤其是在高负载（高容量和高流量）情况下。 如果未使用该功能，建议您禁用模块输出。 由于存在依赖性问题，因此不建议禁用该模块。

## 解决方案

>[!WARNING]
>
>我们强烈建议先在[暂存/集成环境](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md)上测试更改，然后再将其应用于生产。 我们还建议在进行任何操作之前进行最近备份。

1. 禁用`Magento_Banner`模块输出，如开发人员文档中的[禁用模块输出](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output)中所述。 您需要使用的模块名称为`Magento_Banner`。
1. 部署代码。 对于云基础架构上的Adobe Commerce，请按照开发人员文档中的[部署您的存储库](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production)文章中的说明进行部署。
1. 禁用模块输出后，该菜单不再出现在管理员中。
1. 您不会再在&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]**&#x200B;下看到“横幅”或“动态”选项。 若要再次显示选项，请[启用模块输出](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/files/disable-module-output?lang=en#disable-module-output-in-a-simple-deployment)。

