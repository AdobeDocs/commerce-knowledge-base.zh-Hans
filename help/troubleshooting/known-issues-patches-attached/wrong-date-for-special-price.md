---
title: 特殊价格的日期错误
description: 本文为与产品特价“起始”日期不正确相关的已知Adobe Commerce 2.2.2问题提供了一个补丁，前提是界面区域设置不同的管理员更改了它的值。
exl-id: fc109550-951e-4900-97e3-4ff3e7e5a395
feature: Orders, Personalization, User Account
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# 特殊价格的日期错误

本文为与产品特价“起始”日期不正确相关的已知Adobe Commerce 2.2.2问题提供了一个补丁，前提是界面区域设置不同的管理员更改了它的值。

## 问题

设置/更改产品的特殊价格时，当前日期和时间将作为`special_from_date`属性的值保存在数据库中（在编辑产品时不可见）。 如果您编辑特殊价格并将管理员用户帐户设置为其他界面区域设置，则可能会将错误值设置为`special_from_date`，因为解析不同区域设置的日期格式时出现问题。

<u>重现步骤</u>：

先决条件：管理员用户区域设置为英语（美国）。

1. 登录到Commerce管理员。
1. 转到管理员用户帐户设置。
1. 将“Interface Locale（接口区域设置）”设置为“Ukrainian（乌克兰）”。
1. 单击&#x200B;**保存帐户**。
1. 转到&#x200B;**目录** > **产品**。
1. 选择任意产品。
1. 在产品页上，单击&#x200B;**高级定价**。
1. 添加特殊价格。
1. 保存产品。
1. 重复步骤7 - 9。
1. 转到&#x200B;**系统** > **操作日志**。
1. 检查产品更新的日志。

<u>预期的结果</u>：

特殊价格的开始日期应为当前日期。

<u>实际结果</u>：

该特价的价格起始日期是将来的几年中的某个日期，从而阻止该特价生效。

## 解决方案

应用该修补程序将防止再次发生问题。 要更正日期设置不正确的产品的数据，请在应用修补程序后重新设置特殊价格。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-11605\_EE\_2.2.2\_COMPOSER\_v1.patch](assets/MDVA-11605_EE_2.2.2_COMPOSER_v1.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* Adobe Commerce（所有部署方法） 2.2.2

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署2.1.0 - 2.1.18、2.2.0 - 2.2.5
* 云基础架构上的Adobe Commerce 2.1.11-2.1.18、2.2.0-2.2.5

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
