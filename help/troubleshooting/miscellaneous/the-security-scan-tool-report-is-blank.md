---
title: 安全扫描工具报告为空白
description: 本文修复了安全扫描工具显示空白页面而非实际报告的问题。 列入允许列表要解决此问题，可能需要将工具使用的IP添加到防火墙。
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 安全扫描工具报告为空白

本文修复了安全扫描工具显示空白页面而非实际报告的问题。 列入允许列表要解决此问题，可能需要将工具使用的IP添加到防火墙。

## 受影响的产品和版本：

* Adobe Commerce（所有部署方法）和Magento Open Source，所有版本

## 问题

<u>重现步骤</u>：

1. 按照用户指南中的[安全扫描](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html)中的说明，配置安全扫描工具以检查您的网站。
1. 在“操作”列中，选择&#x200B;**运行扫描**。

<u>预期的结果</u>：

查看报表完成通知和打开报表的功能。

<u>实际结果</u>：

无通知且无报告可用。

## 原因

出现此问题的原因可能是安全扫描工具无法访问您的网站。 这意味着网站已关闭且完全无法访问，或者安全扫描工具被阻止。

## 解决方案

尝试打开您的网站。

* 列入允许列表如果页面加载成功，您可能需要将安全扫描工具使用的IP添加到防火墙。 在端口80和443上使用以下IP：52.87.98.44、34.196.167.176、3.218.25.102。
* 如果该网站未加载并返回&#x200B;*“处理您的请求时出错”*&#x200B;消息，请检查您的网站是否存在错误。

## 相关阅读

* 在我们的开发人员文档中[上线并启动](https://devdocs.magento.com/guides/v2.3/cloud/live/live.html?_ga=2.73579601.273749082.1559572284-888339099.1547722854#security-scan)。
* 用户指南中的[安全扫描](https://docs.magento.com/m2/ee/user_guide/magento/security-scan.html)。
