---
title: 可用于Adobe Commerce的安全更新 — [!DNL APSB25-08]
promoted: true
description: 为Adobe Commerce和Magento Open Source 2.4.7-beta1、2.4.7-p3、2.4.6-p8、2.4.5-p10、2.4.4-p11及更早的版本应用独立的修补程序以修复 [!DNL critical, important, and moderate vulnerabilities] 。
feature: Compliance, Security
role: Developer
source-git-commit: 45c6486dea10b37aa8114467bbd7be0c7f9f86f6
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# 可用于Adobe Commerce的安全更新 — [!DNL APSB25-08]

2025年2月11日，Adobe发布了Adobe Commerce和Magento Open Source的定期安全更新。 此更新解决了[[!DNL critical, important]和 [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html)漏洞。 成功利用这些漏洞可能会导致执行任意代码、绕过安全功能以及提升权限。 更多信息可在[Adobe安全公告([!DNL APSB25-08])此处](https://helpx.adobe.com/security/products/magento/apsb25-08.html)找到。

>[!NOTE]
>
>**为了帮助确保尽快应用以上安全公告中列出的[!DNL CVE-2025-24434]的修正，Adobe还发布了解析[!DNL CVE-2025-24434]的隔离修补程序。 这允许商家单独应用修复，由于潜在的集成问题，延迟的风险较少。**

**请尽快应用最新的安全更新。 如果未这样做，则您将容易遭受这些安全问题的攻击，而Adobe在帮助进一步修复该问题方面将没有多少手段。**

>[!NOTE]
>
>如果您在应用安全修补程序/隔离修补程序时遇到任何问题，请联系支持服务。

## 受影响的产品和版本

云基础架构上的Adobe Commerce、Adobe Commerce内部部署和Magento Open Source：

* 2.4.7-beta1及更早版本
* 2.4.7-p3及更早版本
* 2.4.6-p8及更低版本
* 2.4.5-p10及更早版本
* 2.4.4-p11及更早版本

## 适用于Adobe Commerce on Cloud和Adobe Commerce内部部署软件的解决方案

为帮助解决受影响产品和版本的漏洞，必须应用[!DNL CVE-2025-24434]独立修补程序。

## 隔离的补丁程序详细信息

使用以下附加的隔离修补程序：

[vuln-28982-composer-patch.zip](assets/vuln-28982-composer-patch.zip)

## 如何应用独立修补程序

解压缩文件，并参阅我们的支持知识库中的[如何应用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的编辑器修补程序以获取说明。

## 仅适用于Adobe Commerce on Cloud商家 — 如何判断是否已应用独立的修补程序

考虑到无法轻松检查问题是否已修补，您可能希望检查[!DNL CVE-2025-24434]隔离修补程序是否已成功应用。

>[!NOTE]
>
><u>您可以执行以下步骤，以文件`VULN-27015-2.4.7_COMPOSER.patch` **为例**</u>：

1. [安装质量修补程序工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
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

* [Adobe安全公告([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [可用于Adobe Commerce的最新安全更新](https://helpx.adobe.com/security/products/magento.html)
