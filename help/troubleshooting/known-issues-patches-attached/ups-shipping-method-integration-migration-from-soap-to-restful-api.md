---
title: ’[!DNL UPS] 装运方法集成迁移自 [!DNL SOAP] 到 [!DNL RESTful API]’
promoted: true
description: 应用修补程序以处理 [!DNL UPS] 装运方法集成迁移自 [!DNL SOAP] 到 [!DNL RESTful API] 适用于Adobe Commerce 2.4.4的 — 2.4.6-pX。
feature: Shipping/Delivery
role: Developer
exl-id: 8ab5d4a8-0155-4b2c-ab67-d0bd2f949a07
source-git-commit: 7785a37e033bc2bea5b6a1509c337289e7b871cb
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# [!DNL UPS] 装运方法集成迁移自 [!DNL SOAP] 到 [!DNL RESTful API]

>[!NOTE]
>
>如果您在上传本文中的三个修补程序中的任何一个 **2023年10月10日**，您应该再次为您的2.4.4+/2.4.5+/2.4.6+版本的Adobe Commerce/Magento Open Source应用本文现在发布的这些修补程序之一，因为否则，您将无法选择和配置特定的 [!DNL UPS] 中的配送方式 **[!DNL Admin configuration]**，并且您必须启用所有这两项功能。 这些新修补程序与以前发布的修补程序兼容。

本文提供了一个修补程序，用于解决的问题 [!DNL United Parcel Service (UPS)] 装运方法集成迁移自 [!DNL SOAP] 到 [!DNL RESTful API] 适用于Adobe Commerce 2.4.4的 — 2.4.6-pX。

根据对 [!DNL UPS API] 安全模式， [!DNL UPS] 已实施 [!DNL OAuth 2.0] 面向所有人的安全模型 [!DNL APIs] (更多详情请参见 [[!DNL UPS] 开发人员门户访问密钥迁移指南](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914))，以增强整体安全性，从而减少欺诈并提供 [!DNL API] 功能。

此更改将影响我们当前的 [!DNL UPS] Adobe Commerce中的配送方法集成实施，需要我们修复当前实施并从中迁移 [!DNL SOAP API] 到 [!DNL RESTful API] 能够支持 [!DNL OAuth 2.0] 身份验证协议。

**从2024年6月开始**，Adobe Commerce商家将无法使用我们当前的 [!DNL UPS] 集成，因此我们将发布此修补程序，以便允许Adobe Commerce 2.4.4+/2.4.5+/2.4.6+商家迁移到最新版本 [!DNL UPS REST APIs].

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

此 [!DNL UPS] 已发布 [安全更新 [!DNL API]](https://developer.ups.com/oauth-developer-guide?loc=en_US&amp;sp_rid=NTA5MzQ1OTE2NjEyS0&amp;sp_mid=72989914).

## 解决方案

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的修补程序：

要解决2.4.4+、2.4.5+和2.4.6+版本中的问题，必须将相应的修补程序应用于下面的Adobe Commerce/Magento Open Source版本。

## Patch

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的修补程序：

### 对于版本2.4.4、2.4.4-pX：

* [AC-9363_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip](assets/AC-9646_UPS_Shipping_Method_Migration_REST_API_2.4.4x_COMPOSER.patch.zip)

### 对于版本2.4.5、2.4.5-pX：

* [AC-9358_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip](assets/AC-9647_UPS_Shipping_Method_Migration_REST_API_2.4.5x_COMPOSER.patch.zip)

### 对于版本2.4.6、2.4.6-pX：

* [AC-9345_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip](assets/AC-9648_UPS_Shipping_Method_Migration_REST_API_2.4.6x_COMPOSER.patch.zip)

## 如何应用修补程序

解压缩文件并查看 [如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) 在我们的支持知识库中获取说明。

## 如何判断是否已应用修补程序

考虑到无法轻松检查问题是否已修补，您可能需要检查修补程序是否已成功应用。 它使用(例如： *AC-9363*)作为要检查的修补程序。

<u>为此，您可以执行以下步骤</u>：

1. [安装 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. 运行以下命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9363|Status"
   ```

1. 您应该会看到类似以下内容的输出，其中AC-9363返回 *已应用* 状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9363_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
