---
title: 不处理来自管理员和前端不同域的网络来源付款
description: 本文为已知的Adobe Commerce 2.3.0限制提供了一个修补程序，该修补程序与无法同时从storefront和Commerce Admin处理网络源支付（如果它们位于不同的域）有关。
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# 不处理来自管理员和前端不同域的网络来源付款

本文为已知的Adobe Commerce 2.3.0限制提供了一个修补程序，该修补程序与无法同时从storefront和Commerce Admin处理网络源支付（如果它们位于不同的域）有关。

>[!NOTE]
>
>核心的Adobe Commerce网络源支付集成自2.3.3之后已被弃用，并将在2.4.0中完全删除。请改用Marketplace中的[正式扩展](https://marketplace.magento.com/cybersource-global-payment-management.html)。

## 问题

之前实施的网络源集成仅允许从一个域处理支付。 因此，如果您的Adobe Commerce店面与Commerce管理员不在同一域中，那么当您尝试在管理员中使用赛博源下订单时，会收到以下错误：“*Load denied by X-Frame-Options： https://%your\_domain%/cybersource/SilentOrder/TokenResponse/不允许跨域分帧。* ...”

<u>重现步骤</u>：

1. 在其他子域上设置管理员。
1. 在&#x200B;**商店** >设置> **配置** > **销售** > **付款方式** > **网络资源**&#x200B;下为商店配置网络资源。
1. 转到&#x200B;**销售** > **订单**。
1. 创建新订单。
1. 创建新客户。
1. 输入客户详细信息。
1. 输入订单详细信息（产品、发运方法）。
1. 选择Cybersource作为付款方法。
1. 提交订单。

<u>预期结果</u>：下订单时没有问题。

<u>实际结果</u>：“订单”页显示加载图标，但从未下达订单。 该错误显示在控制台中。

## 解决方案

附加的修补程序为与Cybersource的集成提供了改进。 应用修补程序后，您需要为管理员中的网络资源再创建一个配置文件，以便处理付款，并在Commerce管理员中的网络资源配置中添加所需的凭据，其位于&#x200B;**商店** >设置> **配置** > **销售** > **付款方式** > **网络资源**&#x200B;下。

>[!NOTE]
>
>该改进包括在Adobe Commerce本地和云基础架构2.2.9和2.3.1中。

## Patch

本文附有几个修补程序，这些修补程序适用于不同的版本。 要下载补丁程序，请向下滚动到文章末尾，然后单击文件名，或单击以下链接：

* [下载MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [下载MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [下载MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [下载MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## 兼容的Adobe Commerce版本

修补程序是为修补程序文件名中注明的特定版本创建的。 例如，MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch是为Adobe Commerce 2.1.9创建的，它是用于此版本的最佳修补程序。

这些修补程序还与以下版本兼容：

* Adobe Commerce内部部署2.1.3-2.1.17；云基础架构上的Adobe Commerce 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce内部部署2.2.0-2.2.3；云基础架构上的Adobe Commerce 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2.2\_COMPOSER\_v2.patch)
* Adobe Commerce内部部署2.2.4-2.2.7；云基础架构上的Adobe Commerce 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce内部部署2.2.8、2.3.0；云基础架构上的Adobe Commerce 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
