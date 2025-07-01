---
title: cURL错误60： SSL证书已过期
description: 本文说明如何在收到cURL错误60后检查上次部署分支的时间：云基础架构上的Adobe Commerce上的主分支或集成分支中的SSL证书已过期。
exl-id: 74f1db7e-ee2b-4e27-8fcc-fe462a9e72c3
feature: Configuration
role: Developer
source-git-commit: dcaae51408534b82181b268f60905b123e240900
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# cURL错误60： SSL证书已过期

本文说明如何检查在收到`cURL error 60`后上次部署分支的时间： [!DNL SSL certificate]在Adobe Commerce云基础架构上的[!DNL Master]或[!DNL Integration]分支中过期。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 原因

这些分支中的[!DNL SSL certificates]仅在30天内有效，并且该分支可能在30天内未重新部署。

该错误将类似于以下内容：

```cURL
cURL error 60: SSL certificate problem: certificate has expired
```

>[!NOTE]
>
>这些证书不是由[!DNL Let's Encrypt]或[!DNL DigiCert]等已知外部证书颁发机构(CA)签名的。 出于测试和开发目的，这些证书由Adobe平台管理，并且默认情况下在浏览器或curl中不受信任，除非您明确信任颁发证书的根。

## 解决方案

检查上次部署分支的时间。 如果超过30天的阈值，则重新部署分支。

检查上次执行部署的时间的两种方法：

* [方法1：使用 [!DNL magento-cloud] CLI](#meth2)。
* [方法2：打开 [!DNL Project URL]](#meth3)。

如果部署已成功完成，则将自动续订[!DNL SSL certificate]。

如果部署失败并且您需要解决该问题的帮助，请[提交支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hans#submit-ticket)。

### 方法1：使用[!DNL magento-cloud] CLI {#meth2}

运行此命令： `magento-cloud activity:list --type=environment.push`

### 方法2：打开[!DNL Project URL] {#meth3}

转到，例如： `https://demo.magento.cloud/#/projects/<project>/environments/<environment>`，然后检查上次执行部署的时间。

## 相关阅读

在我们的开发人员文档中：

* [Cloud Manager API： SSLCertificates](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/SSLCertificates)
* [设置Fastly：设置SSL/TLS证书](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates)

在我们的支持知识库中：

* [自定义SSL证书过期信息](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/custom-ssl-certificate-expiration-information.html?lang=zh-Hans)
* 云基础架构上Adobe Commerce的[SSL (TLS)证书](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/ssl-tls-certificates-for-magento-commerce-cloud-faq.html?lang=zh-Hans)
