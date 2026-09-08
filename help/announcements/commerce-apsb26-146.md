---
title: 需要为Adobe Commerce提供关键安全更新的紧急操作(APSB26-146)
description: Adobe发布了安全公告APSB26-146，旨在应对Adobe Commerce中的零日漏洞CVE-2026-75650。 了解如何应用修补程序并轮换凭据。
autotag-review: '2026-09-07T17:27:44.037Z'
TQID: 'https://experienceleague.adobe.com/ADVRRn85--ZgWtPdi4qA49fsDPVW976N4MYWp26taho'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c32adafa-ed01-4b31-997e-2413013911b0
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: e95fb4ca696be9f6d348ff66196565797575f74a
workflow-type: tm+mt
source-wordcount: 954
ht-degree: 0%

---


# 需要采取紧急行动：Adobe Commerce提供了关键安全更新(APSB26-146)

>[!IMPORTANT]
>
>这是与CVE-2026-75650相关的紧急更新。 Adobe知道，CVE-2026-75650已在野外Adobe Commerce商家中遭到利用。

2007年9月，Adobe发布了一项影响Adobe Commerce和Magento Open Source的关键安全更新。 Adobe发现了Adobe Commerce中的零日漏洞，并发布了安全更新(APSB26-146)以解决该问题。 该漏洞允许未经身份验证的攻击者对受影响的安装执行任意代码(CVE-2026-75650)。

Adobe已发布安全公告APSB26-146，其中介绍了此漏洞。 公告可从此处获取：

[可用于Adobe Commerce的安全更新| APSB26-146](https://helpx.adobe.com/security/products/magento/apsb26-146.html)

本文介绍了如何为Adobe Commerce和Magento Open Source的当前版本及早期版本应用修补程序。

## 描述

受影响的产品和版本：

Adobe Commerce版本：

* 2.4.9-2026-8月及更早版本
* 2.4.8-2026-8月及更早版本
* 2.4.7-2026-8月及更早版本
* 2.4.6-2026-8月及更早版本
* 2.4.5-2026-8月及更早版本
* 2.4.4-2026-8月及更早版本

Adobe Commerce B2B版本：

* 1.5.3-2026-8月及更早版本
* 1.5.2-2026-8月及更早版本
* 1.4.2-2026-8月及更早版本
* 1.3.4-2026-8月及更早版本
* 1.3.3-2026-8月及更早版本

Magento Open Source版本：

* 2.4.9-2026-8月及更早版本
* 2.4.8-2026-8月及更早版本
* 2.4.7-2026-8月及更早版本
* 2.4.6-2026-8月及更早版本

## 解决方法

### 适用于Adobe Commerce on Cloud、Adobe Commerce内部部署和Magento Open Source的解决方案

>[!NOTE]
>
>现在，适用于CVE-2026-75650的修补程序与2.4.4 - 2.4.7之间的所有Adobe Commerce和Magento Open Source版本都兼容。 请参阅下表并下载适用于您的版本的修补程序。

为帮助解决受影响产品和版本的漏洞，您必须应用以下&#x200B;**修补程序**（取决于您的版本）并旋转加密密钥。

| 版本号 | Patch |
|---|---|
| 2.4.9至2026年8月， 2.4.8至2026年8月， 2.4.7至2026年8月， 2.4.6至2026年8月， 2.4.5至2026年8月， 2.4.4至2026年8月， 2.4.9至2026年7月， 2.4.8至2026年7月， 2.4.7至2026年7月， 2.4.6-2026-7月，2.4.5-2026-7月，2.4.4-2026-7月，2.4.8-p5,2.4.8-p4,2.4.8-p3,2.4.7-p10,2.4.7-p9,2.4.6-p15,2.4.6-p14,2.4.5-p16,2.4.4-p18,2.4.4-p18 | [修补程序VULN-39341-composer-patches.zip](https://repo.magento.com/patch/VULN-39341-composer-patches.zip) |
| 2.4.8-p3和2.4.8-p2 | [VULN-39341_248-p3.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p3-patch.zip) |
| 2.4.8-p1， 2.4.8 | [VULN-39341_248-p1.patch.zip](https://repo.magento.com/patch/VULN-39341-248-p1-patch.zip) |
| 2.4.7-p8和2.4.7-p7 | [VULN-39341_247-p8.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p8-patch.zip) |
| 2.4.7 - 2.4.7-p6 | [VULN-39341_247-p5.patch.zip](https://repo.magento.com/patch/VULN-39341-247-p5-patch.zip) |
| 2.4.6-p13、2.4.6-p12、2.4.5-p15、2.4.5-p14、2.4.4-p16、2.4.4-p15 | [VULN-39341_246-p13.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p13-patch.zip) |
| 2.4.6 - 2.4.6-p11， 2.4.5 - 2.4.5-p13， 2.4.4 - 2.4.4-p14 | [VULN-39341_246-p11.patch.zip](https://repo.magento.com/patch/VULN-39341-246-p11-patch.zip) |


{style="table-layout:auto"}

### 如何应用修补程序

解压缩文件，并在我们的支持知识库中参阅[如何应用Adobe提供的编辑器修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)获取相关说明。

### 确认应用了修补程序（仅限Cloud Mertors上的Adobe Commerce）

考虑到无法轻松确定问题是否已修补，建议您检查CVE-2026-75650修补程序是否已成功应用。

为此，您可以使用文件`VULN-39341_Hotfix_COMPOSER.patch`作为示例，执行以下步骤：

1. [安装质量修补程序工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage#install)。
1. 运行命令： `vendor/bin/magento-patches -n status | grep "39341\|Status"`。
1. 您应该会看到类似于以下内容的输出，其中示例VULN-39341返回Applied状态：

| ID | 标题 | 类别 | Origin | 状态 | 详细信息 |
|---|---|---|---|---|---|
| 不适用 | .../m2-hotfixes/VULN-39341_Hotfix_COMPOSER.patch | 其他 | 本地 | 已应用 | 修补程序类型：自定义 |

### 在应用补丁程序后旋转身份证明

要完全解决此问题，请不仅轮换您的加密密钥，而且轮换已使用该密钥加密或公开的所有凭据，包括服务器、API和集成凭据。

>[!NOTE]
>
>加密密钥用于加密集成令牌、支付网关凭据和系统授权的自动化令牌。 仅旋转加密密钥不会使可能已公开的凭据失效。 在来源（例如，在支付网关或第三方服务）旋转所有关联的凭据，而不仅仅是在Commerce中。

要旋转凭据，请执行以下步骤：

1. 应用修补程序。
1. 启用维护模式。
1. 禁用cron执行（云命令上的Commerce： `vendor/bin/ece-tools cron:disable`）。
1. [旋转加密密钥](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key?lang=en)。
1. 旋转所有Admin面板用户密码。
1. 停用并重新生成所有REST/SOAP/GraphQL集成令牌(**[!UICONTROL System]** > **[!UICONTROL Extensions]** > **[!UICONTROL Integrations]**)。
1. 为任何连接的第三方应用程序轮换OAuth客户端密钥。
1. 在提供商级别（Stripe、Braintree、Adyen、PayPal等）轮换支付网关API凭据。
1. 旋转数据库凭据。
1. 轮换SSH/部署密钥和任何cron或系统授权的服务帐户凭据。
1. 轮换API密钥，用于运输、税务和其他集成的第三方扩展。
1. 刷新缓存。
1. 启用cron执行（云命令上的Commerce： `vendor/bin/ece-tools cron:enable`）。
1. 禁用维护模式。
1. 仅限Commerce on Cloud：重新部署以应用新的数据库凭据。

### 安全更新

可用于Adobe Commerce的安全更新：

* [Adobe安全公告(APSB26-146)](https://helpx.adobe.com/security/products/magento/apsb26-146.html)
* [可用于Adobe Commerce的最新安全更新](https://helpx.adobe.com/security/products/magento.html)

### 相关阅读

在《Adobe Commerce安装指南》中[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode?lang=en)
