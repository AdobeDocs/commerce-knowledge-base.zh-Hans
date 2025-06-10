---
title: 验证 [!DNL Fastly] 凭据时出错
description: 本文为用户在验证 [!DNL Fastly] 凭据时遇到错误的问题提供了解决方案。
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 838f0c5d55c29d026dc37a8f7e5214b9880a4353
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# 验证[!DNL Fastly]凭据时出错

本文说明如何解决在验证[!DNL Fastly]凭据时遇到的&#x200B;*令牌过期*&#x200B;错误。

如果您出于安全原因需要旋转（循环）您的[!DNL Fastly] API令牌，则本文中概述的步骤也适用。 在这些情况下，您应提交Adobe Commerce支持票证以请求新的[!DNL Fastly] API令牌。

## 问题

* 验证[!DNL Fastly]凭据时出现错误。
* 您怀疑您的[!DNL Fastly]令牌可能已泄漏，例如，无意间在支持票证中共享或发布在公共论坛上的令牌。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）：所有版本
* 扩展或技术（[!DNL Fastly]、[!DNL New Relic]等）版本[!DNL Fastly]

## 解决方案

1. 请确保您具有正确的[!DNL Fastly]服务ID和API令牌，然后再次尝试验证。 有关详细说明，请参阅我们的开发人员文档中的[测试 [!DNL Fastly] 凭据](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)。
1. 如果凭据验证失败，请运行以下curl命令以确认服务的状态：

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. 如果上述命令返回类似于`{"msg":"Token $TOKEN expired at 2021-09-28T02:03:37Z"}`的错误，请提交支持票证以请求新的API令牌。 收到新令牌后，更新环境中的配置。

   要了解如何提交支持工单，请参阅我们的支持知识库中的[Adobe Commerce帮助中心用户指南>支持工单](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets)。

   >[!NOTE]
   >
   >切勿直接在票证中共享任何密码或有效的/活动的API令牌，因为出于安全原因，我们将必须撤销当前令牌并生成一个新的令牌。
   >
   >Adobe Commerce支持部门有权访问令牌，因此您无需在票证中包含此信息。

1. 如果命令未返回错误，请确保您运行的是[!DNL Fastly]扩展的最新版本。 如果您使用的是1.2.203之前的旧版本，则必须先单击&#x200B;**[!UICONTROL Save Config]**，然后才能测试凭据。

## 我们的开发人员文档中的相关阅读：

* 适用于Adobe Commerce的[Cloud > [!DNL Fastly] > [!DNL Fastly] 服务帐户和凭据](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/fastly?lang=en#fastly-service-account-and-credentials)

* 适用于Adobe Commerce的[Cloud >设置 [!DNL Fastly] >测试 [!DNL Fastly] 凭据](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration?lang=en#test-the-fastly-credentials)
