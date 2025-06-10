---
title: 可用于Adobe Commerce的安全更新 — [!DNL APSB25-50]
promoted: true
description: 为Adobe Commerce 2.4.8、2.4.7-p5、2.4.6-p10、2.4.5-p12、2.4.4-p13及更早版本应用独立的修补程序以修复 [!DNL critical and important vulnerabilities] 。
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# 可用于Adobe Commerce的安全更新 — [!DNL APSB25-50]

2025年6月10日，Adobe发布了Adobe Commerce和Magento Open Source的定期安全更新。 此更新解决了[[!DNL critical] 和 [!DNL important]](https://helpx.adobe.com/security/severity-ratings.html)漏洞。 成功利用这些漏洞可能会导致绕过安全功能、权限提升和任意代码执行。

更多信息可在[Adobe安全公告([!DNL APSB25-50])此处](https://helpx.adobe.com/security/products/magento/apsb25-50.html)找到。

>[!NOTE]
>
>**为了帮助确保尽快应用以上安全公告中列出的[!DNL CVE-2025-47110]的修正，Adobe还发布了一个解析[!DNL CVE-2025-47110]的隔离修补程序。 这允许商家单独应用修复，由于潜在的集成问题，延迟的风险较少。**

**请尽快应用最新的安全更新。 如果您未能做到这一点，您将容易遭受这些安全问题的攻击，而Adobe在帮助进一步修复该问题方面手段有限。**

您可以在此处阅读有关[我们的独立修补程序部署过程的更多信息。](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>对于Managed Services上的Adobe Commerce客户，您的客户成功工程师可以提供有关应用补丁程序的其他指导。

>[!NOTE]
>
>如果您在应用安全修补程序/隔离修补程序时遇到任何问题，请联系支持服务。

提醒您，您可以在此处找到[可用于Adobe Commerce的最新安全更新。](https://helpx.adobe.com/security/products/magento.html)

## 受影响的产品和版本

Adobe Commerce（所有部署方法）：

* 2.4.8
* 2.4.7-p5及更早版本
* 2.4.6-p10及更早版本
* 2.4.5-p12及更早版本
* 2.4.4-p13及更早版本

## 问题

### I. CVE-2025-47110：在Adobe Commerce 2.4.7-p4中通过服务器端模板注入存储XSS

<u>受影响的产品和版本</u>：

Adobe Commerce（所有部署方法）：

* 2.4.8
* 2.4.7-p5及更早版本
* 2.4.6-p10及更早版本
* 2.4.5-p12及更早版本
* 2.4.4-p13及更早版本

<u>解决方案</u>：

对于Adobe Commerce版本：

* 2.4.8
* 2.4.7、2.4.7-p1、2.4.7-p2、2.4.7-p3、2.4.7-p4、2.4.7-p5
* 2.4.6、2.4.6-p1、2.4.6-p2、2.4.6-p3、2.4.6-p4、2.4.6-p5、2.4.6-p6、2.4.6-p7、2.4.6-p8、2.4.6-p10
* 2.4.5、2.4.5-p1、2.4.5-p2、2.4.5-p3、2.4.5-p4、2.4.5-p5、2.4.5-p6、2.4.5-p7、2.4.5-p8、2.4.5-p9、2.4.5-p10、2.4.5-p11、2.4.5-p12
* 2.4.4、2.4.4-p1、2.4.4-p2、2.4.4-p3、2.4.4-p4、2.4.4-p5、2.4.4-p6、2.4.4-p7、2.4.4-p8、2.4.4-p9、2.4.4-p10、2.4.4-p11、2.4.4-p12、2.4.4-p13

**应用以下隔离的修补程序或升级到最新的安全修补程序。**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### 二、 VULN-31547：marketplace.magento.com中反映的XSS +一键式影响IMS实例的ATO问题

<u>受影响的产品和版本</u>：

Adobe Commerce（所有部署方法）：

* 2.4.8

<u>解决方案</u>：

对于Adobe Commerce版本：

* 2.4.8

**应用以下隔离的修补程序或升级到最新的安全修补程序。**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## 如何应用独立修补程序

解压缩文件，并在我们的支持知识库中参阅[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)获取相关说明。

## 仅适用于Adobe Commerce on Cloud商家 — 如何判断是否已应用独立的修补程序

考虑到无法轻松检查问题是否已修补，您可能希望检查[!DNL CVE-2025-47110]隔离修补程序是否已成功应用。

>[!NOTE]
>
><u>您可以执行以下步骤，使用文件`VULN-27015-2.4.7_COMPOSER.patch` **作为示例**</u>：

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

* [Adobe安全公告([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [可用于Adobe Commerce的最新安全更新](https://helpx.adobe.com/security/products/magento.html)
