---
title: Adobe Commerce管理员URL位置已披露
description: 本文提供了一个适用于Adobe Commerce安全问题的修补程序，可在该修补程序中披露管理员面板的URL位置。 知道URL位置可以更轻松地自动实施攻击。
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Adobe Commerce管理员URL位置已披露

本文提供了一个适用于Adobe Commerce安全问题的修补程序，可在该修补程序中披露管理员面板的URL位置。 知道URL位置可以更轻松地自动实施攻击。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.X.X
* Adobe Commerce内部部署2.X.X
* Magento Open Source2.X.X

## 问题

在Magento Open Source和Adobe Commerce中发现了一个问题，该问题可用于公开管理员面板的URL位置。 虽然目前没有理由认为此问题会导致直接危害，但知道URL位置可能会更容易自动化攻击。

## 解决方案

要解决此问题，请应用本文附带的修补程序。 要下载它，请单击以下链接：

* 下载[PRODSECBUG-2432\_EE\_2.1.17\_composer.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) — 适用于版本2.1.13-2.1.17、Adobe Commerce、Magento Open Source
* 下载[PRODSECBUG-2432\_EE\_2.2.8\_composer.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) — 适用于版本2.2.0-2.2.8的所有版本
* 下载[PRODSECBUG-2432\_EE\_2.3.1\_composer.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) — 适用于版本2.3.0-2.3.1的所有版本

如果您没有看到产品/版本的修补程序，请升级到最新的安全版本，然后应用该修补程序。

Adobe强烈建议尽快应用修补程序，即使您未遇到任何攻击症状。

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 其他安全建议

Adobe列入允许列表还强烈建议商家部署工具来保护其管理面板，包括双重身份验证、VPN、IP等。 有关详细信息，请参阅以下博客和文档：

* [针对Protect暴力攻击的立即操作](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect您的Magento安装密码猜测新更新](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [安全最佳实践](https://magento.com/security/best-practices/security-best-practices)
* 在Adobe Commerce中为[2.4.x](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)添加并配置双重身份验证
