---
title: 安全扫描工具报告为空白
description: 本文修复了安全扫描工具显示空白页面而非实际报告的问题。 要解决此问题，可能需要将工具使用的IP添加到防火墙。
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%
---
# 安全扫描工具报告为空白

本文修复了安全扫描工具显示空白页面而非实际报告的问题。 要解决此问题，可能需要将工具使用的IP添加到防火墙。

## 受影响的产品和版本：

* Adobe Commerce（所有部署方法）和Magento Open Source（所有版本）

## 问题

<u>重现步骤</u>：

1. 按照用户指南中的[安全扫描](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)中的说明，配置安全扫描工具以检查您的网站。
1. 在“操作”列中，选择&#x200B;**运行扫描**。

<u>预期的结果</u>：

查看报表完成通知和打开报表的功能。

<u>实际结果</u>：

无通知且无报告可用。

## 原因

出现此问题的原因可能是安全扫描工具无法访问您的网站。 这意味着网站已关闭且完全无法访问，或者安全扫描工具被阻止。

## 解决方案

尝试打开您的网站。

* 如果页面加载成功，您可能需要将安全扫描工具使用的IP添加到防火墙。 在端口80和443上使用以下IP： 52.87.98.44、34.196.167.176、3.218.25.102。
* 如果该网站未加载并返回&#x200B;*“处理您的请求时出错”*&#x200B;消息，请检查您的网站是否存在错误。

## 相关阅读

* 在我们的开发人员文档中[上线并启动](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview)。
* 用户指南中的[安全扫描](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)。
