---
title: 如何获取和应用[!UICONTROL security patch]
description: 本文提供了有关如何获取和应用已发布的[!UICONTROL security patch]的说明，但说明不可用。
exl-id: 55f2be73-2ccc-4750-a7bd-3058fc2d5107
source-git-commit: 06bc239cb5b1a894d2a60236a9b32b2b0c4eba80
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# 如何获取和应用[!UICONTROL security patch]

本文提供了有关如何获取和应用已发布的[!UICONTROL security patch]的说明，但说明不可用。

## 受影响的产品和版本

Adobe Commerce On-Premise和Cloud — 所有版本

## 原因

发布的大多数[!UICONTROL Security Patches]都没有应用任何物理文件或修补程序。

## 解决方案


### 案例一：

如果发行说明中提到物理修补程序文件/修补程序：

* 从[https://account.magento.com](https://account.magento.com/downloads/view/)的下载部分下载文件。 （共享访问用户必须首先获得帐户所有者/许可证持有者的下载权限）

**注意事项：**

如果您使用的是较低版本的Adobe Commerce (2.4.4)，则您将自动获得扩展支持。 您的版本必须是下列不支持的版本之一，才能应用最新的可用安全修补程序：

2.4.4 - 2.4.4-p11

不受支持的版本(2.3.x、2.4.0 - 2.4.3)没有资格获得支持，您必须首先升级到受支持的版本才能利用最新的安全修复。

如果您没有扩展支持，可以请求支持人员与您共享修补程序，但是他们将无法解决您在应用修补程序时可能遇到的任何问题/错误。

### 案例二：

如果发行说明中未提及物理修补程序文件/修补程序：

* **云：**

1. 在适用于Commerce的Cloud修补程序下的Cloud Tools Suite (ECE Tools)的最新版本中可能包含/发布了某些[!UICONTROL Security Patches] — 请查看[发行说明](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)，如果发行版中提到安全修补程序，请将包升级到该版本。
1. 如果发行说明未提及安全修复，请继续阅读。

* **云或内部部署：**

* 如果物理修补程序文件/修补程序不可用，请[将Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version) 2.4.X上的Adobe Commerce版本升级到2.4.X-pY的最新修补程序版本。
* 如果物理修补程序文件/修补程序不可用，请[将Adobe Commerce版本On-Premise](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade) 2.4.X升级到最新的修补程序版本2.4.X-pY。

## 相关阅读

* 请参阅《Commerce Cloud基础架构上的Adobe Commerce指南》*中的[Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite)发行说明*。
* 请参阅&#x200B;*Adobe Commerce Infrastructure指南*&#x200B;中的[升级Adobe Commerce版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version)。
