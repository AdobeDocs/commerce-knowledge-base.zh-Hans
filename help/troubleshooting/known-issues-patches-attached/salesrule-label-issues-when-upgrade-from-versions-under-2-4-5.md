---
title: 从版本&amp；lt； 2.4.5升级时，“[!UICONTROL salesRule]标签出现问题”
description: 应用修补程序以处理从Adobe Commerce版本&amp；lt； 2.4.5升级时出现的**[!UICONTROL salesRule]**问题。
exl-id: e1bd6d44-576e-4d91-bab5-32c41e3b8300
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 从低于2.4.5的版本升级时，**[!UICONTROL salesRule]**&#x200B;标签出现问题

Adobe Commerce [2.4.5](/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html)中引入了&#x200B;**[!UICONTROL salesRule]**&#x200B;标签暂存功能。 当您从Adobe Commerce &lt; 2.4.5升级到任何版本>= 2.4.5时，此更改可能会导致问题。升级后，**[!UICONTROL salesRule]**&#x200B;标签可能不匹配。 要解决此问题，应在升级到较新的Adobe Commerce版本后立即应用修补程序。

## 受影响的产品和版本

云基础架构上的Adobe Commerce &lt; 2.4.5

## Patch

使用以下附加的修补程序：

[ACSD-50625_2.4.5-P1.patch.zip](assets/ACSD-50625_2.4.5-p1.patch.zip)

## 如何应用修补程序

1. 按照Commerce指南中[执行升级](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)中的步骤操作。
1. 在&#x200B;**[!UICONTROL Update metadata]**阶段之前应用附加的修补程序。
（您也可以在完成**[!UICONTROL Update metadata]**&#x200B;阶段后应用修补程序，但随后您需要再次运行`bin/magento setup:upgrade`）。
1. 继续执行[执行升级](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html)中的其余步骤。
