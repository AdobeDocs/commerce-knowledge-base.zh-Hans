---
title: 无法验证VAT编号 — 云基础架构上的Adobe Commerce
description: 本文为VAT号码验证过程中出错的问题提供了补丁程序。
exl-id: 9868e888-bad8-4823-acab-4b3804933cb0
feature: Cloud, Customer Service, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 无法验证VAT编号 — 云基础架构上的Adobe Commerce

本文为VAT号码验证过程中出错的问题提供了补丁程序。

## 受影响的产品和版本

所有高达2.3.6的Adobe Commerce内部部署和Adobe Commerce on cloud基础架构版本（包括2.3.5-p1）都受到影响，包括已发布的p1和p2版本。 这包括：

* 2.3.5-p1
* 2.3.5
* 2.3.4 - 2.3.4-p2
* 2.3.3 - 2.3.3-p1
* 2.3.2 -2.3.2-p2
* 2.0.0 - 2.3.1

## 问题

<u>要再现的步骤：</u>

1. 前往&#x200B;**商店** > **配置** > **客户** > **客户配置** > **新建帐户选项**&#x200B;并将&#x200B;**启用自动分配**&#x200B;到&#x200B;**客户组**&#x200B;到&#x200B;*是*。
1. 转到&#x200B;**常规** > **存储信息** >并设置有效的国家/地区和VAT编号。
1. 单击&#x200B;**验证VAT编号**。

<u>预期结果：</u>

验证成功。

<u>实际结果：</u>

显示以下错误：“*验证VAT号码时出错。*”

## 解决方案

应用本文中提供的[patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[MDVA-27623\_EE\_2.3.2-p2\_COMPOSER\_v1.patch](assets/MDVA-27623_EE_2.3.2-p2_COMPOSER_v1.patch.zip)

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
