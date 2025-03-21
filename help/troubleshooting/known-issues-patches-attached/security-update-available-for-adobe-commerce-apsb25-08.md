---
title: 可用于Adobe Commerce的安全更新 — [!DNL APSB25-08]
promoted: true
description: 为Adobe Commerce 2.4.8-beta1、2.4.7-p3、2.4.6-p8、2.4.5-p10、2.4.4-p11及更早版本应用独立的修补程序以修复 [!DNL critical, important, and moderate vulnerabilities] 。
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: d669c097767b5855c6bd747a0ab11b3520f405a0
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# 可用于Adobe Commerce的安全更新 — [!DNL APSB25-08]

2025年2月11日，Adobe发布了Adobe Commerce和Magento Open Source的定期安全更新。 此更新解决了[[!DNL critical, important]和 [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html)漏洞。 成功利用这些漏洞可能导致任意代码执行、绕过安全功能和权限提升。 更多信息可在[Adobe安全公告([!DNL APSB25-08])此处](https://helpx.adobe.com/security/products/magento/apsb25-08.html)找到。

>[!NOTE]
>
>**为了帮助确保尽快应用上面安全公告中列出的[!DNL CVE-2025-24434]的修正，Adobe还发布了可解决[!DNL CVE-2025-24434]的隔离修补程序。 这允许商家隔离应用修复，且由于潜在集成问题导致的延迟风险较低。**

**请尽快应用最新的安全更新。 如果未能做到这一点，您将容易受到这些安全问题的攻击，而Adobe对于进一步修复问题将没有多少帮助。**

>[!NOTE]
>
>如果在应用安全修补程序/隔离修补程序时遇到任何问题，请联系支持服务。

## 受影响的产品和版本

云基础架构上的Adobe Commerce、内部部署的Adobe Commerce和Magento Open Source：

* 2.4.8-beta1及更早版本
* 2.4.7-p3及更早版本
* 2.4.6-p8及更低版本
* 2.4.5-p10及更早版本
* 2.4.4-p11及更早版本

## 适用于Adobe Commerce on Cloud、Adobe Commerce内部部署和Magento Open Source软件的解决方案

为帮助解决受影响的产品和版本的漏洞，必须应用[!DNL CVE-2025-24434]隔离修补程序，具体取决于您的Adobe Commerce/Magento Open Source版本。

## 隔离修补程序详细信息

根据您的Adobe Commerce/Magento Open Source版本，使用以下附加的隔离修补程序：

### 对于版本2.4.8-beta1：

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### 对于版本2.4.7、2.4.7-p1、2.4.7-p2、2.4.7-p3：

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### 对于版本2.4.6、2.4.6-p1、2.4.6-p2、2.4.6-p3、2.4.6-p4、2.4.6-p5、2.4.6-p6、2.4.6-p7、2.4.6-p8：

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### 对于版本2.4.5、2.4.5-p1、2.4.5-p2、2.4.5-p3、2.4.5-p4、2.4.5-p5、2.4.5-p6、2.4.5-p7、2.4.5-p8、2.4.5-p9、2.4.5-p10：

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### 对于版本2.4.4、2.4.4-p1、2.4.4-p2、2.4.4-p3、2.4.4-p4、2.4.4-p5、2.4.4-p6、2.4.4-p7、2.4.4-p8、2.4.4-p9、2.4.4-p10、2.4.4-p11：

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## 如何应用隔离修补程序

解压缩文件，并在我们的支持知识库中参阅[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)获取相关说明。

## 仅适用于Adobe Commerce on Cloud商家 — 如何判断是否已应用独立的修补程序

考虑到无法轻松检查问题是否已修补，您可能希望检查[!DNL CVE-2025-24434]隔离修补程序是否已成功应用。

>[!NOTE]
>
><u>您可以执行以下步骤，以文件`VULN-27015-2.4.7_COMPOSER.patch` **为例**</u>：

1. [安装质量修补程序工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 运行命令： <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您应该会看到与下图类似的输出，其中VULN-27015返回&#x200B;*已应用*&#x200B;状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## 安全更新

可用于Adobe Commerce的安全更新：

* [Adobe安全公告([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [可用于Adobe Commerce的最新安全更新)](https://helpx.adobe.com/security/products/magento.html)