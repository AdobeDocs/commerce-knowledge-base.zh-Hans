---
title: 自定义SSL证书过期信息
description: 本文为使用Adobe提供的SSL证书更新自定义SSL证书时提供了解决方案。
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 自定义SSL证书过期信息

本文为使用Adobe提供的SSL证书更新自定义SSL证书时提供了解决方案。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

Adobe Commerce会在过期前30天自动更新SSL证书。 此自动化不会检查要替换的证书是内部SSL还是自定义第三方SSL，并会在检测到过期时将其替换为有效的内部SSL。 这可能会导致站点所有者和希望拥有站点自定义证书的操作者感到困惑，并且可能会导致其他功能问题，包括但不限于站点中断。

<u>重现步骤</u>

1. 为网站安装的自定义SSL证书。
1. 自动化会检测自定义SSL证书是否在30天后过期。
1. Adobe Commerce会自动将自定义证书替换为内部证书。

<u>预期的结果</u>

Adobe Commerce在运行其自动的SSL证书更新时跳过自定义证书。

<u>实际结果</u>

Adobe Commerce会在过期后30天内更新任何证书。

## 解决方案

当商家选择使用自己的自定义SSL证书时，必须在证书到期前30天以上更新该证书，以确保不会将其替换为内部Adobe Commerce SSL证书。

如果您遇到自定义SSL被内部SSL替换的情况，并且希望将其替换为您更新的自定义SSL证书，请[提交支持请求](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket)，并提供您上载新证书文件的位置。 请包括新SSL的开始日期。 获得此信息后，我们可以继续安装新的SSL证书。

## 相关阅读

* Magento Commerce Cloud的[SSL (TLS)证书：我们的支持知识库中的常见问题解答](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md)。
* [命令行工具引用：开发人员文档中的magento-cloud证书:add](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd)。
* 在开发人员文档中[启动项核对清单](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/launch/checklist)。
* 访问用户指南中的[站点范围分析工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool)。
