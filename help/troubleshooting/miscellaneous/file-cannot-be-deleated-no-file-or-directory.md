---
title: “无法删除文件。 警告！ 取消链接： “ [!DNL Admin]”中没有此类文件或目录错误
description: 本文提供了解决出现错误*无法删除文件问题的方案。 警告！在执行 [!DNL Javascript/CSS] 刷新操作时，从 [!DNL Admin] 中取消链接没有此类文件或目录错误*。
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *无法删除该文件。 警告！unlink：没有来自[!DNL Admin]的文件或目录错误*

本文提供了解决您看到错误&#x200B;*无法删除文件问题的方案。 警告！unlink：执行[!DNL JavaScript/CSS]刷新时，[!DNL Commerce Admin]中没有此类文件或目录错误*。

## 受影响的产品和版本

* Adobe Commerce 2.4.0 - 2.4.6，所有部署方法

## 问题

执行[!DNL JS/CSS]刷新时出现错误：

*无法删除“/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b”文件。 警告！unlink(/app/pub/static/_cache/merged/.nfsa42d0e64799fd1000000001b)：没有这样的文件或目录*

或：您在[!DNL Admin]中看到上述错误，和/或在[!DNL New Relic]或部署日志中看到类似错误。

或者：您无法访问高级报告，并且analytics_collect_data cron作业失败，出现以下错误：

*无法删除“/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0”文件。 警告！unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0)：没有这样的文件或目录*

<u>要再现的步骤：</u>

方法1：

1. 登录到[!DNL Admin]。
1. 转到&#x200B;**[!UICONTROL System]** > **[!UICONTROL Cache Management]**。
1. 单击&#x200B;**[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**。

方法2：

1. 登录到[!DNL Admin]。
1. 转到&#x200B;**[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**。
1. 更改[!UICONTROL Base URL]或[!UICONTROL Base URL (Secure)]。
1. 单击&#x200B;**[!UICONTROL Save Config]**。

## 解决方案

如果您在云基础架构上的Adobe Commerce上并且安装了[!DNL magento/magento-cloud-patches] 1.0.22，其中包括修补程序，则无需单独安装ACSD-50165。

Cloud基础架构上的Adobe Commerce：将Commerce的云修补程序升级到1.0.22 （**或更高版本**），该修补程序包含以下修补程序： [Commerce的云修补程序](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html)。

Adobe Commerce内部部署：使用[Quality Patches Tools > Usage](/docs/commerce-operations/tools/quality-patches-tool/usage.html)应用ACSD-50165。 ACSD-50165修补程序附带[!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## 相关阅读

* Commerce工具指南中的[[!DNL Quality Patches Tool] >发行说明](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)。
* [[!DNL Quality Patches Tool]： Commerce Tools指南中的搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
