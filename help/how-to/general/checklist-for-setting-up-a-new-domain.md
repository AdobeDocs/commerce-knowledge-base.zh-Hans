---
title: 设置新 [!DNL domain]的清单
description: 这是一份清单，说明如何在Adobe Commerce中在云基础架构上设置新的 [!DNL domain] 。
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: f7b246088e3580922bd3389b2992e5dd8f97ff7a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# 设置新[!DNL domain]的清单

此核对清单说明如何在Adobe Commerce中在云基础架构上设置新的[!DNL domain]。 无论您是添加新域还是替换当前域，此规则都适用。 在获得新的暂存环境后，此标准也适用（请参阅步骤4）。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，[所有支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 如何设置新域

### 步骤1 — 这是否适用于[!DNL Integration, Staging]或[!DNL Production environment]？

* 不支持&#x200B;**[!DNL Integration]**： [!DNL Custom domains]。 您必须改用此方法： [设置多个网站或商店：在我们的用户指南中配置本地安装](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hans#add-new-domains)。
* **[!DNL Staging]**：转到&#x200B;**步骤2**。
* **[!DNL Production]**：转到&#x200B;**步骤3**。

### 步骤2 - [!DNL Staging environment]：您是在[!DNL Pro]还是[!DNL Starter]？

* **[!DNL Pro]**： **提交请求**&#x200B;以将域添加到[!DNL Fastly, Nginx]，并配置[!DNL SSL certificate]（如有必要，还将配置[!DNL Sendgrid domain]）。 完成配置后，[使用 [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hans#update-dns-configuration-with-development-settings)更新 [!DNL DNS] 配置。

>[!NOTE]
>
>您可以自己将新[!DNL domain]添加到[!DNL Fastly]，方法是像在我们的用户指南中的[[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=zh-Hans#manage-domains)一样，在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]**&#x200B;中更新[!DNL Admin]中的配置。
>
>如果您无法添加域，可能是由于以下原因之一：
>
>1. 您正在将域迁移到已在您自己的[!DNL Fastly]服务中配置的云环境。 在这种情况下，提交请求并请求委派域。
>1. 您正在将域从Starter迁移到Pro。 在这种情况下，请提出进一步援助请求。

* 暂存环境中不支持&#x200B;**[!DNL Starter]**： [!DNL Custom domains]。

### 步骤3 - [!DNL Production environment]：您是在[!DNL Pro]还是[!DNL Starter]？

* **[!DNL Pro]**： **提交请求**&#x200B;以将域添加到[!DNL Fastly, Nginx]，并配置[!DNL SSL certificate]（如有必要，作为[!DNL Sendgrid domain]）。 配置完毕后，请继续&#x200B;**步骤4**。

>[!NOTE]
>
>您可以自己将新[!DNL domain]添加到[!DNL Fastly]，方法是在我们的用户指南的&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=zh-Hans#manage-domains)中更新[!DNL Admin]中的配置。
>
>
>如果您无法添加域，可能是由于以下原因之一：
>
>1. 您正在将域从内部部署迁移到云环境，该环境已在您自己的[!DNL Fastly]服务中配置。 在这种情况下，提交请求并请求委派域。
>1. 您正在将域从Starter迁移到Pro。 在这种情况下，请提出进一步援助请求。

* **[!DNL Starter]**：将[!DNL domain]添加到您项目的&#x200B;**[!DNL Domains]**&#x200B;选项卡中，然后&#x200B;**提交请求**&#x200B;以提供[!DNL SSL certificate]的&#x200B;**[!DNL ACME Challenge Key]**。

### 步骤4 - [!DNL domain]是否处于活动状态？

* **是**：[使用[!UICONTROL production]设置更新 [!DNL DNS] 配置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=zh-Hans#update-dns-configuration-with-production-settings)。
* **否**：[使用[!UICONTROL development]设置更新 [!DNL DNS] 配置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=zh-Hans#update-dns-configuration-with-development-settings)。

## 相关阅读

* [设置多个网站或商店：在我们的用户指南中新增 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=zh-Hans#add-new-domains)。
* 由于源遮蔽，[网站无法访问](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/production-site-not-accessible-due-to-origin-cloaking)
