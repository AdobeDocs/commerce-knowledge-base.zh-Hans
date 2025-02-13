---
title: Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0兼容包修补程序
description: 本文提供了一个修补程序，用于在Cloud基础架构2.4.7-p4上为新的 [!DNL HIPAA] 包1.2.0添加与Adobe Commerce的兼容性
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0兼容包修补程序

本文提供了一个修补程序，用于在Cloud基础结构2.4.7-p4上为新的&#x200B;**[!DNL HIPAA]包1.2.0**&#x200B;添加与Adobe Commerce的兼容性。

此问题将在版本2.4.7-p5版本中修复。

## 受影响的版本和产品

Cloud基础架构上的Adobe Commerce 2.4.7-p4及更早版本

## 先决条件

* Adobe已配置您的Adobe Commerce帐户以访问&#x200B;**[!DNL HIPAA Ready]**&#x200B;扩展。 请参阅Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview)上的[[!DNL HIPAA] 准备工作，以了解我们的&#x200B;**Adobe Commerce：入门指南**&#x200B;中的更多详细信息。
* 访问[repo.magento.com](https://repo.magento.com)以安装扩展。 有关密钥生成和获取必要权限的信息，请参阅&#x200B;**Adobe Commerce：安装指南**&#x200B;中的[获取您的身份验证密钥](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys)。

## 问题

[!DNL HIPAA]包1.1.0与Adobe Commerce 2.4.7x版本行不兼容。

## 解决方案

通过此修补程序，在Cloud Infrastructure 2.4.7-p4上运行Adobe Commerce的商家将能够使用[!DNL HIPAA]包1.2.0。

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0仅与Adobe Commerce 2.4.7-p5兼容。 如果要将与[!DNL HIPAA] 1.2.0的兼容性添加到Adobe Commerce 2.4.7-p4，请安装提供的修补程序。<br><u>如果您不在Adobe Commerce 2.4.7-p4上，则必须先升级到Adobe Commerce 2.4.7-p4，才能使用此修补程序</u>。**

要修复云基础架构2.4.7-p4上有关Adobe Commerce的问题，您应应用以下修补程序：

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## 如何应用修补程序

解压缩文件，并在我们的支持知识库中参阅[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)获取相关说明。

## 仅适用于Adobe Commerce on Cloud商家 — 如何判断是否已应用修补程序

考虑到无法轻松检查问题是否已修补，您可能需要检查修补程序是否已成功应用。

>[!NOTE]
>
><u>您可以按照以下步骤执行此操作，使用文件`VULN-27015-2.4.7_COMPOSER.patch` **作为示例**</u>：

1. [安装质量修补程序工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 运行命令： <br>
   ![cve-2024-34102-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您应该看到类似于以下内容的输出： **<u>，其中此处使用的示例VULN-27015</u>**&#x200B;返回&#x200B;*已应用*&#x200B;状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
