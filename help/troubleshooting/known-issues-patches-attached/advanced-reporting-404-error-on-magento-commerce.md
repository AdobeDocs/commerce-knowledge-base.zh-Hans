---
title: '[!DNL Advanced Reporting] Adobe Commerce出现404错误'
description: 本文为商户在尝试访问[[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html)时遇到404错误时的Adobe Commerce问题提供了修补程序。 安装此修补程序后，用户将能够访问 [!DNL Advanced Reporting]。
exl-id: bac61704-44fe-4bd2-b342-af90219231ef
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Adobe Commerce上的[!DNL Advanced Reporting] 404错误

本文提供了一个修补程序，用于解决商家尝试访问[[!DNL Advanced Reporting]](https://experienceleague.adobe.com/docs/commerce-admin/config/general/advanced-reporting.html)时出现404错误时的Adobe Commerce问题。 安装此修补程序后，用户将能够访问[!DNL Advanced Reporting]。

要检查此修补程序是否可以解决此问题，请先使用以下命令查看日志：

`zgrep analytics_collect_data var/log/support_report.log var/log/support_report.log.1.gz`

如果您看到`Not valid cipher`错误，请应用附加的修补程序。

## 受影响的产品和版本

Adobe Commerce 2.2.6

## 问题

商家尝试访问[!DNL Advanced Reporting]时收到404错误。

## 解决方案

要解决此问题，请应用本文附带的修补程序。 要下载它，请向下滚动到文章结尾并单击文件名，或单击以下链接： [下载MDVA-18980\_EE\_2.2.6\_COMPOSER\_v1](assets/MDVA-18980_EE_2.2.6_COMPOSER_v1.patch.zip)

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
