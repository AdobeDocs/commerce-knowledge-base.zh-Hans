---
title: 云基础架构上Adobe Commerce的SSL (TLS)证书
description: 本文提供了有关在我们的云基础架构上获取Adobe Commerce站点的SSL (TLS)证书问题的快速解答。
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 43c3e5f95c4b54e235140cd5b3978d3887af5ee1
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# 云基础架构上Adobe Commerce的SSL (TLS)证书

本文提供了有关在我们的云基础架构上获取Adobe Commerce站点的SSL (TLS)证书问题的快速解答。

## Adobe提供哪些SSL/TLS证书？

Adobe提供了一个域验证的[让我们加密SSL/TLS证书](https://letsencrypt.org/)以提供来自[!DNL Fastly]的安全HTTPS流量。 Adobe为云基础架构上的每个Adobe Commerce提供一个证书专业规划架构、暂存和Adobe Commerce云基础架构入门规划架构环境，以保护该环境中的所有域。

## 证书涵盖哪些内容？

对于专业计划架构，将创建一个SSL证书，该证书将用于测试和生产专用环境。 Platform-as-a-Service (PaaS)集成环境之外的每个专用环境都将具有此证书，以用于分配给该环境的URL。

对于入门计划架构和PaaS集成环境，将有一个默认技术域，该域配置有环境并由单独的证书进行保护。

## 如何为现有证书添加新域？

要将域添加到[!DNL Fastly]中的服务，请执行以下操作：

1. 将DNS中的域指向prod.magentocloud.map.fastly.net ，最长等待6小时。
1. [提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求在Nginx配置中添加此域（如果之前未添加）。

## 如何请求证书？

用例1

如果您尚未启动网站，则可能已从客户技术顾问(CTA)处收到ACME挑战CNAME。 如果您无法立即将DNS指向生产URL，并且需要提前创建SSL证书，则只需要ACME质询即可。

用例2

如果您的网站已经上线和/或您可以立即指向将用于您的实时网站的URL，则无需请求ACME CNAME。 在云基础架构站点上向您的Adobe Commerce添加必要的URL并将DNS指向[!DNL Fastly]后，HTTP验证将起作用，并且首次创建您的SSL证书或使用其他URL更新您的证书。

## 我可以使用自己的SSL/TLS证书吗？

您可以提供自己的SSL/TLS证书，而不是使用Adobe提供的[Let&#39;s Encrypt证书](https://letsencrypt.org/)。

但是，此过程需要额外的设置和维护工作。 您首先需要为网站的域名（或通用名称）生成证书签名请求(CSR)，并将其提供给您的SSL供应商以提供SSL证书。

获得SSL证书后，请提交[Adobe Commerce支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，或与您的CTA合作将自定义托管的证书添加到云环境。

* 如果不再使用这些域，这些域将自动从我们的系统中清除，并且无需执行进一步操作。
* 如果您已经拥有证书，请使用SFTP（SSH文件传输协议）客户端将其上载到服务器上不可访问Web的文件位置，然后[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，让他们知道文件路径。

>[!WARNING]
>
>切勿将证书文件直接上传到票证，这一点很重要。 否则，证书将被视为泄露，Adobe需要请求新的证书。
>文件应通过SFTP上载到服务器 — 不使用任何其他方法，如将文件提交到存储库（只应对不包含敏感数据的不可变文件执行此操作）。

## 证书的名称

SSL证书的名称仅与主URL有关，它是由第一个URL命名的主要主机名，必须与要验证和创建的主机名匹配。 如果您有几个URL，它们将作为使用者备用名称条目添加到证书中。 如果您的多个URL指向云基础架构网站上的一个Adobe Commerce，则您将只有一个通用名称URL认证，该认证随后将附加使用者替代名称，以使用SSL保护您的网站。

## 证书的“公用名”字段中将显示哪个域？

证书上显示的域只是添加到TLS证书的第一个域，它填充&#x200B;**公用名** (**CN**)字段，浏览器首先显示此名称。 **主题替代名称** (**SAN**)字段包含TLS证书的所有DNS名称。 无法更改或请求显示的“公用名”。

## 我可以使用通配符TLS证书吗？

通配符TLS证书只能与您的自定义证书一起使用，不能与Adobe Commerce Let&#39;s Encrypt证书一起使用。 作为我们的TLS优化的一部分，Adobe将终止对通配符TLS证书的支持。 我们正在识别并联系使用通配符证书与Adobe的Let&#39;s Encrypt证书并在Adobe Commerce的[!DNL Fastly]控制台中配置的商家。 我们要求将这些通配符证书替换为精确域，以确保TLS覆盖。 要替换通配符TLS证书，请访问[!DNL Fastly]插件的[域部分](https://devdocs.magento.com/cloud/cdn/configure-fastly-customize-cache.html#manage-domains)。 从此处，可以添加确切的域，并且可以删除通配符。 请注意，DNS需要指向[!DNL Fastly]，这些新域才能通过CDN路由。 添加域并更新DNS后，将配置匹配的[Let&#39;s Encrypt](https://letsencrypt.org/)证书。 如果不使用通配符删除指向[!DNL Fastly]的域，Adobe将删除共享证书。 如果您未配置URL FQDN并在DNS中设置相同的URL FQDN，则可能会导致站点中断。 因此，您应该确认配置的URL在其DNS中也具有指向[!DNL Fastly]的一对一匹配项。

## 如果我的域不再指向Adobe Commerce，我应该怎么做？

如果您的域不再指向Adobe Commerce，请将其从[!DNL Fastly]/Adobe Commerce系统中删除。 请参阅[!DNL Fastly] [删除域](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain)以了解详情。 虽然不必将域指向Adobe Commerce，但请确认是否需要顶级域TLS证书。 如果需要顶级域，请更新您的DNS以指向Adobe Commerce。 如果它已经指向Adobe Commerce，请更新您的CAA记录以包含[lets-encrypt](https://letsencrypt.org/)。 如果执行这些步骤，您将看到使用证书覆盖的必要次要URL更新了LE证书&#x200B;。

## 相关阅读

在我们的开发人员文档中[配置SSL/TLS证书](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates)
