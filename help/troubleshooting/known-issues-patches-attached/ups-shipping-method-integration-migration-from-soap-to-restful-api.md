---
title: “[!DNL UPS]配送方式集成从 [!DNL SOAP] 迁移到 [!DNL RESTful API]”
promoted: true
description: 应用修补程序以处理Adobe Commerce 2.4.4 - 2.4.6-pX的 [!DNL UPS] 送货方法集成从 [!DNL SOAP] 迁移到 [!DNL RESTful API] 的问题。
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 6694bb1e041e6285f5bd5a05a1c37b7062521f52
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL UPS]配送方式集成从[!DNL SOAP]迁移到[!DNL RESTful API]

>[!NOTE]
>
>如果您在&#x200B;**2024年6月6日之前上传了本文中的三个修补程序中的任何一个**：如果您因为未使用[!DNL Metric System/SI]测量（千克和厘米）而遇到此问题，则应当再次为您的Adobe Commerce/Magento Open Source的2.4.4+/2.4.5+/2.4.6+版本重新应用本文中发布的这些新的更新修补程序之一，因为否则，您将无法在&#x200B;**[!DNL Admin configuration]**&#x200B;的[!DNL UPS]配送方法中选择&#x200B;**千克**&#x200B;和&#x200B;**厘米**&#x200B;的[!DNL Metric System/SI]测量。 这些新修补程序与以前发布的修补程序兼容。 此问题将在计划于&#x200B;**2024年6月11日**&#x200B;发行的即将发布的Adobe Commerce版本2.4.7-p1的范围内永久修复。

>[!NOTE]
>
>如果您在2023年10月10日&#x200B;**之前上传了本文中的三个修补程序中的任意一个**，则应当再次为您的2.4.4+/2.4.5+/2.4.6+版本的Adobe Commerce/Magento Open Source应用本文中现在发布的这些修补程序之一，因为否则，您将无法在&#x200B;**[!DNL Admin configuration]**&#x200B;中选择和配置特定的[!DNL UPS]送货方法，并且必须启用所有这些方法。 这些新修补程序与以前发布的修补程序兼容。

本文提供了一个修补程序，用于解决Adobe Commerce 2.4.4 - 2.4.6-pX的[!DNL United Parcel Service (UPS)]配送方式集成从[!DNL SOAP]迁移到[!DNL RESTful API]时出现的问题。

根据[!DNL UPS API]安全模型的最新更新，[!DNL UPS]已为所有[!DNL APIs]实施了[!DNL OAuth 2.0]安全模型（[[!DNL UPS] 开发人员门户访问密钥迁移指南](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)中提供了更多详细信息）以增强整体安全性，从而减少欺诈行为并提供增强的[!DNL API]功能。

此更改影响我们在Adobe Commerce中当前的[!DNL UPS]配送方法集成实施，并要求我们修复当前的实施并从[!DNL SOAP API]迁移到[!DNL RESTful API]以便能够支持[!DNL OAuth 2.0]身份验证协议。

**从2024年6月开始**，Adobe Commerce商家将无法使用我们当前的[!DNL UPS]集成进行交易，因此我们将发布此修补程序，以便让Adobe Commerce 2.4.4+/2.4.5+/2.4.6+商家迁移到最新的[!DNL UPS REST APIs]。

此问题将在Adobe Commerce/Magento Open Source版本2.4.7中修复，此修复还将包含在2023年10月的2.4.7-beta2版本中。

## 受影响的产品和版本

云基础架构和内部部署以及Magento Open Source上的Adobe Commerce：

* 2.4.4
* 2.4.4像素
* 2.4.5
* 2.4.5-pX
* 2.4.6
* 2.4.6像素

## 原因

[!DNL UPS]已发布其 [!DNL API][&#128279;](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914)的安全更新。

如果您将欧盟（其他来源可能遇到相同问题）作为装运的来源地，这将导致[!DNL UPS REST]请求中出错：
“*装运不能以KGS/IN、LBS/CM或OZS/CM作为其度量单位。*”

## 解决方案

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的修补程序：

要解决2.4.4+、2.4.5+和2.4.6+版本中的问题，必须将相应的修补程序应用于下面的Adobe Commerce/Magento Open Source版本。

## Patch

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的修补程序：

### 对于版本2.4.4、2.4.4-pX：

* [AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-11984_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### 对于版本2.4.5、2.4.5-pX：

* [AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-11983_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### 对于版本2.4.6、2.4.6-pX：

* [AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-11916_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## 如何应用修补程序

解压缩文件，并参阅我们的支持知识库中的[如何应用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的编辑器修补程序以获取说明。

## 如何判断是否已应用修补程序

考虑到无法轻松检查问题是否已修补，您可能需要检查修补程序是否已成功应用。 该选项使用（示例： *AC-9363*）作为要检查的修补程序。

<u>您可以通过以下步骤执行此操作</u>：

1. [安装 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 运行以下命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 您应该会看到类似以下内容的输出，其中AC-9363返回&#x200B;*已应用*&#x200B;状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
