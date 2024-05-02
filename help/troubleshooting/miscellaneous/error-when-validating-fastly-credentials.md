---
title: 验证Fastly凭据时出错
description: 本文为用户在验证Fastly凭据时遇到错误的问题提供了解决方案。
exl-id: 02104731-6666-47a6-abc6-215812f09915
feature: Configuration
role: Developer
source-git-commit: 831a928dbe8fd6b37f3fe9ad5dc35ee80e11a578
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# 验证Fastly凭据时出错

本文为用户在验证Fastly凭据时遇到错误的问题提供了解决方案。

## 问题

用户在验证Fastly凭据时遇到错误。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）：所有版本
* 扩展或技术(Fastly、New Relic等) 版本Fastly

## 解决方案

1. 请确保您具有正确的Fastly服务ID和API令牌，并尝试重新验证。 有关详细说明，请参阅 [测试Fastly凭证](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials) 在我们的开发人员文档中。
1. 如果凭据验证失败，请运行以下curl命令以确认服务的状态：

   ```curl
   curl -H "Fastly-Key: <API key>" https://api.fastly.com/service/<service ID>/version/active
   ```

1. 如果上述命令返回类似以下内容的错误： *{“msg”：“令牌$TOKEN已于2021-09-28T02过期:03:37Z”}*，提交支持票证以请求新的API令牌。

   要了解如何提交支持工单，请参阅 [Adobe Commerce帮助中心用户指南>支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#support-tickets) 在我们的支持知识库中。

   >[!NOTE]
   >
   >切勿直接在票证中共享任何密码或有效的/活动的API令牌，因为出于安全原因，我们将必须撤销当前令牌并生成一个新的令牌。

1. 如果命令未返回错误，请确保您运行的是最新版本的 [!DNL Fastly] 扩展。 如果您使用的是1.2.203之前的旧版本，则必须先单击 **[!UICONTROL Save Config]** 才能测试凭据。

## 我们的开发人员文档中的相关阅读：

* [Cloud for Adobe Commerce > Fastly > Fastly服务帐户和凭据](https://devdocs.magento.com/cloud/cdn/cloud-fastly.html#fastly-service-account-and-credentials)

* [Cloud for Adobe Commerce >设置Fastly >测试Fastly凭据](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#test-the-fastly-credentials)
