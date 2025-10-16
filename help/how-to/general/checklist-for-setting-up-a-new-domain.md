---
title: 设置新 [!DNL domain]的清单
description: 这是一份清单，说明如何在Adobe Commerce中在云基础架构上设置新的 [!DNL domain] 。
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 552a290b50f9e0c5fa740f26092c57bac447fe68
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# 设置新[!DNL domain]的清单

此核对清单说明如何在Adobe Commerce中在云基础架构上设置新的[!DNL domain]。 无论您是添加新域还是替换当前域，此规则都适用。 在获得新的暂存环境后，此标准也适用（请参阅步骤4）。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，[所有支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 如何设置新域

>[!NOTE]
>
>在继续域设置之前，请确保：
>
>在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**&#x200B;下，所有基础URL都配置为使用HTTPS，其作用域为正确的网站或商店视图。
>&#x200B;> [已启用强制TLS](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/redirect-http-to-https-for-all-pages-on-cloud-force-tls#token_type=bearer&expires_in=10799996)，以在云基础架构上的Adobe Commerce站点中将所有HTTP流量重定向到HTTPS。

### 步骤1 — 这是否适用于[!DNL Integration, Staging]或[!DNL Production environment]？

* 不支持&#x200B;**[!DNL Integration]**： [!DNL Custom domains]。 您必须改用此方法： [设置多个网站或商店：在我们的用户指南中配置本地安装](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains)。
* **[!DNL Staging]**：转到&#x200B;**步骤2**。
* **[!DNL Production]**：转到&#x200B;**步骤3**。

### 步骤2 - [!DNL Staging environment]：您是在[!DNL Pro]还是[!DNL Starter]？

* **[!DNL Pro]**： **提交请求**&#x200B;以将域添加到[!DNL Fastly, Nginx]，并配置[!DNL SSL certificate]（如有必要，还将配置[!DNL Sendgrid domain]）。 完成配置后，[使用 [!DNL DNS]  [!DNL development settings]更新](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)配置。

>[!NOTE]
>
>对于PRO架构，添加新域需要向Adobe Commerce提交支持请求。 虽然某些客户可以通过Admin Console手动配置Fastly，但这仅适用于有限的情况，例如域未绑定到其他Fastly服务或项目时。 但是，始终需要Nginx配置，并且此步骤必须由Adobe处理。 因此，建议且最可靠的方法是提交[支持票证](https://experienceleague.adobe.com/home?support-tab=home#support)，并让Adobe管理整个域设置过程。


* 暂存环境中不支持&#x200B;**[!DNL Starter]**： [!DNL Custom domains]。

### 步骤3 - [!DNL Production environment]：您是在[!DNL Pro]还是[!DNL Starter]？

* **[!DNL Pro]**： **提交请求**&#x200B;以将域添加到[!DNL Fastly, Nginx]，并配置[!DNL SSL certificate]（如有必要，作为[!DNL Sendgrid domain]）。 配置完毕后，请继续&#x200B;**步骤4**。

>[!NOTE]
>
>您可以自己将新[!DNL domain]添加到[!DNL Fastly]，方法是在我们的用户指南的[!DNL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** **[!UICONTROL Domains]**&#x200B;[[!DNL Manage domains]&#x200B;中更新](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains)中的配置。
>
>
>如果您无法添加域，可能是由于以下原因之一：
>
>1. 您正在将域从内部部署迁移到云环境，该环境已在您自己的[!DNL Fastly]服务中配置。 在这种情况下，提交请求并请求委派域。
>1. 您正在将域从Starter迁移到Pro。 在这种情况下，请提出进一步援助请求。

* **[!DNL Starter]**：将[!DNL domain]添加到您项目的&#x200B;**[!DNL Domains]**&#x200B;选项卡中，然后&#x200B;**提交请求**&#x200B;以提供&#x200B;**[!DNL ACME Challenge Key]**&#x200B;的[!DNL SSL certificate]。

### 步骤4 - [!DNL domain]是否处于活动状态？

* **是**：[使用 [!DNL DNS] 设置更新[!UICONTROL production]配置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings)。
* **否**：[使用 [!DNL DNS] 设置更新[!UICONTROL development]配置](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings)。

### 步骤5 — 是否在`magento-vars.php`中配置了域重定向？

配置域后，您需要[修改](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables)文件中的变量`magento-vars.php`，以将域定向到相应的网站/商店URL。

### 步骤6 - [!DNL domain]配置是否已验证？

如果您在新域的&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;中添加了新商店、商店组和网站，请检查以下部分是否出现在您的`app/etc/config.php`文件中，例如：

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

这意味着您以前曾通过运行[包中的](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build)命令在Build`config:dump`上设置`ece-tools`SCD。

如果您发现创建的新商店/网站未显示在`app/etc/config.php`文件中，请确保再次运行该命令以将`config.php`文件与对数据库的更改同步，然后提交`config.php`文件并重新部署。 这有助于将新商店/网站的静态内容部署到相应的文件路径。

## 相关阅读

* [设置多个网站或商店：在我们的用户指南中新增 [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains)。
* 由于源遮蔽，[网站无法访问](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26856)
