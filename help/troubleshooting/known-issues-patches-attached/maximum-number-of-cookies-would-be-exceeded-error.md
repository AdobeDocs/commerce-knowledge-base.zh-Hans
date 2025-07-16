---
title: Adobe Commerce中出现超出Cookie最大数量的错误
description: 了解如何解决发生错误（说明超出了Cookie最大数量）的Adobe Commerce问题。
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
exl-id: 5c42ea7a-f023-4d34-8417-bb470efc3b84
source-git-commit: 87e98607ee5e1cc41e4266836fd09531a290725e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# 在Adobe Commerce中超出&#x200B;*Cookie最大数量*&#x200B;错误

本文提供了补丁以解决以下错误：在Adobe Commerce中超出&#x200B;*最大Cookie数*。

## 受影响的产品和版本

Adobe Commerce（所有部署方法）2.4.4 - 2.4.7，并应用了以下修补程序之一：

* 使用[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/release-notes)应用了MDVA-12304修补程序
* [可用于Adobe Commerce的安全更新 — APSB25-08](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-27149)
* [适用于 [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)的云修补程序

## 问题

与Adobe Commerce中的Cookie相关的问题导致错误日志中出现以下错误：

*报告。警告：无法发送Cookie。 将超出Cookie的最大数量。*

### 原因

出现此问题的原因是，允许的最大Cookie数设置为&#x200B;*50*。

## 解决方案

1. 如果您使用[!DNL Quality Patches Tool (QPT)]应用了MDVA-12304修补程序，请将其删除。

   * 对于云基础架构上的Adobe Commerce，从`.magento.env.yaml`中删除修补程序。
   * 对于Adobe Commerce内部部署，请运行以下命令来还原修补程序：

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. 根据您的Adobe Commerce版本应用附加的修补程序：

   * 对于版本2.4.4-p12、2.4.5-p11、2.4.6-p9和2.4.7-p4，请应用[ACSD-64710修补程序](assets/acsd-64710_2.4.5-p11.patch.zip)。

   * 对于版本2.4.4-p13、2.4.5-p12、2.4.6-p10、2.4.7-p5和2.4.8，请应用[ACSD-65562修补程序](assets/acsd-65562_2.4.5-p12.patch.zip)。

### 相关阅读

* Adobe Commerce升级指南中的[应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/upgrade-guide/patches/apply)
* [在Adobe Commerce实施行动手册中大规模分发Adobe Commerce修补程序的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale)
* Commerce on Cloud指南中的Commerce Cloud Tools Suite [发行说明](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite)。
