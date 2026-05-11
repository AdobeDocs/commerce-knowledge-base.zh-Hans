---
title: 配置Adobe AI API密钥后，无法查看多个SaaS数据空间
description: 本文提供了一种解决方案，来解决在为Adobe AI配置API密钥后您只能看到一个SaaS数据空间的问题。
exl-id: e13041da-b122-4684-8287-42132931f47a
feature: REST, Saas, Observability
role: Developer
source-git-commit: 61f5a526a0c36c91739103c0802bc9794a425f38
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# 配置Adobe AI API密钥后，无法查看多个SaaS数据空间

为Commerce服务(如Adobe AI服务（产品推荐或实时搜索）或Adobe Commerce的支付服务)配置API密钥后，您可能会在Commerce Services Connector中看到多个SaaS数据空间。 根据产品权利和部署类型，连接器仅显示一个SaaS数据空间，这属于预期行为。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）：所有版本
* Magento Open Source：所有版本
* 扩展或技术（Fastly、New Relic等）、Adobe AI（产品推荐/实时搜索）

## 问题

配置Adobe AI API密钥后，系统仅显示一个SaaS数据空间。

## 原因

可用SaaS数据空间的数量取决于与Commerce帐户关联的产品权利以及所使用的服务类型。

## 解决方案

通常，可用SaaS数据空间的数量取决于Commerce许可证：

* Adobe Commerce：一个生产数据空间和两个测试数据空间
* Magento Open Source：一个生产数据空间，没有测试数据空间

对于Payment Services，默认行为是：

* 默认情况下，Adobe Commerce （*Cloud或内部部署*）上的付款服务有三个数据空间：
* 一个生产数据空间
* 两个测试数据空间
* 默认情况下，Magento Open Source上的Payment Services具有一个数据空间

拥有多个云项目或内部部署（*实时/生产*）安装的客户还可以通过提交支持请求来请求每个项目或实例的其他生产和测试数据空间。

使用Adobe支付服务的Magento Open Source客户还可以请求额外的数据空间。 在提交支持请求以添加测试数据空间之前，请联系支付团队进行事先批准。

>[!NOTE]
> * 请勿在多个环境中同时使用相同的SaaS数据空间。 如果跨环境重用生产或测试数据空间，则数据可能会变得混合，并且可能需要清理。
> * 默认情况下，Adobe Commerce (*Cloud/On-Prem*)上的付款服务有三个数据空间。
> * 默认情况下，Magento Open Source上的支付服务有一个数据空间。
> 要请求其他数据空间，请执行以下操作：
> * 使用Adobe支付服务的Magento Open Source客户可以请求额外的数据空间。 在提交支持请求以获取测试数据空间之前，请联系支付团队进行事先批准。
> * 拥有多个云项目或内部部署（*实时/生产*）安装的客户还可以通过提交支持请求来请求每个项目或实例的其他生产和测试数据空间。

## 重新关联的阅读

[SaaS数据空间配置](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas?lang=en#saas-data-space-provisioning)
