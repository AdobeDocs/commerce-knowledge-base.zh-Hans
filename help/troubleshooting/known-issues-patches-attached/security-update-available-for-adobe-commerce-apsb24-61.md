---
title: 可用于Adobe Commerce的安全更新 — [!DNL APSB24-61]
promoted: true
description: 为仅运行 [!DNL Apache]的Adobe Commerce 2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10及更早版本实例应用隔离修补程序以修复 [!DNL CVE-2024-39397] 。
feature: Compliance, Security
role: Developer
source-git-commit: 76ff7669a0a57925a176e08031e0789ced0a7f0e
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 可用于Adobe Commerce的安全更新 — [!DNL APSB24-61]

2024年8月13日，Adobe发布了Adobe Commerce、Magento Open Source和Adobe Commerce Webhooks插件的定期安全更新。
此更新解决了[[!DNL critical, important]和 [!DNL moderate]](https://helpx.adobe.com/cn/security/severity-ratings.html)漏洞。 成功利用此漏洞可能会导致执行任意代码、读取任意文件系统、绕过安全功能以及权限提升。 公告是[Adobe安全公告([!DNL APSB24-61])](https://helpx.adobe.com/cn/security/products/magento/apsb24-61.html)。

>[!NOTE]
>
>以上安全公告中列出的&#x200B;**[!DNL CVE-2024-39397]仅在使用[!DNL Apache] Web服务器时适用。**&#x200B;为了帮助确保尽快应用此漏洞的修复，Adobe还发布了解决[!DNL CVE-2024-39397]问题的独立修补程序。

**请尽快应用最新的安全更新。 如果您未能做到这一点，您将容易遭受这些安全问题的攻击，而Adobe帮助进行补救的手段有限。**

>[!NOTE]
>
>如果您在应用安全修补程序/隔离修补程序时遇到任何问题，请联系支持服务。

## 受影响的产品和版本

Adobe Commerce on Cloud、Adobe Commerce内部部署和Magento Open Source：

* 2.4.7-p1及更早版本
* 2.4.6-p6及更低版本
* 2.4.5-p8及更低版本
* 2.4.4-p9及更低版本

## 适用于Adobe Commerce on Cloud、Adobe Commerce本地软件和Magento Open Source的解决方案

为帮助解决受影响产品和版本的漏洞，必须应用[!DNL CVE-2024-39397]独立修补程序。

## 隔离的补丁程序详细信息

使用以下附加的隔离修补程序：

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## 如何应用独立修补程序

解压缩文件，并参阅我们的支持知识库中的[如何应用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hans)提供的编辑器修补程序以获取说明。

## 仅适用于Adobe Commerce on Cloud商家 — 如何判断是否已应用独立的修补程序

考虑到无法轻松检查问题是否已修补，您可能希望检查[!DNL CVE-2024-39397]隔离修补程序是否已成功应用。

<u>您可以执行以下步骤，以文件`VULN-27015-2.4.7_COMPOSER.patch`为例</u>：

1. [安装质量修补程序工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
1. 运行命令： <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您应该会看到类似以下内容的输出，其中VULN-27015返回&#x200B;*已应用*&#x200B;状态：

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

* [Adobe安全公告([!DNL APSB24-61])](https://helpx.adobe.com/cn/security/products/magento/apsb24-61.html)
