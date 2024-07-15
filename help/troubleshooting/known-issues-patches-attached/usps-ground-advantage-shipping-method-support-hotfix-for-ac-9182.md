---
title: “[!DNL USPS] Ground Advantage配送方式支持AC-9182的修补程序”
promoted: true
description: 应用补丁以处理Adobe Commerce 2.4.4 - 2.4.6-p2的 [!DNL USPS] Ground Advantage配送方法问题AC-9182。
feature: Shipping/Delivery
role: Developer
exl-id: b6871d19-3d02-4026-82e6-3545f4ab7159
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# [!DNL USPS] Ground Advantage配送方式支持AC-9182的修补程序

本文提供了一个修补程序，用于解决Adobe Commerce 2.4.4 - 2.4.6-p2中新&#x200B;**[!DNL USPS]Ground Advantage**&#x200B;配送方法的AC-9182问题。

2023年7月9日，美国邮政局([!DNL USPS])发布了一种新的配送方式[[!DNL USPS] Ground Advantage](https://www.usps.com/ship/ground-advantage.htm)。

这种新的配送方式正在取代目前三种主要的配送方式：

* [!DNL USPS]零售场
* [!DNL USPS]第一类包服务
* [!DNL USPS]包裹选择地面

[[!DNL USPS] 宣布](https://faq.usps.com/s/article/USPS-Ground-Advantage#how_it_works)从2023年9月30日开始，将停止使用这三种配送方式，所有客户都必须改用新的&#x200B;**[!DNL USPS]Ground Advantage**&#x200B;方法。

因此，在2023年9月30日之后，所有使用USPS配送方法的Adobe Commerce商户将无法再使用这三种传统配送方法从[!DNL USPS]获得配送费。

此问题将在即将发布的2023年10月版本2.4.6-p3、2.4.5-p5和2.4.4-p6的仅安全补丁发行范围内修复。

## 受影响的产品和版本

云基础架构和内部部署以及Magento Open Source上的Adobe Commerce：

* 2.4.4
* 2.4.4-p1
* 2.4.4 - p2
* 2.4.4 - p3
* 2.4.4-p4
* 2.4.4 - p5
* 2.4.5
* 2.4.5-p1
* 2.4.5 - p2
* 2.4.5-p3
* 2.4.5-p4
* 2.4.6
* 2.4.6-p1
* 2.4.6 - p2

## 原因

[!DNL USPS]进行了[!DNL API]更新。

## 解决方案

要解决2.4.4、2.4.5和2.4.6版本中的问题，必须应用下面的AC-9182修补程序。

## Patch

该修补程序已附加到本文。 要下载它，请单击以下链接：

[AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip](assets/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.zip)

## 如何应用修补程序

解压缩文件，并参阅我们的支持知识库中的[如何应用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html)提供的编辑器修补程序以获取说明。

## 如何判断是否已应用修补程序

考虑到无法轻松检查问题是否已修补，您可能需要检查AC-9182修补程序是否已成功应用。

<u>您可以通过以下步骤执行此操作</u>：

1. [安装 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
1. 运行以下命令：

   ```bash
   vendor/bin/magento-patches -n status |grep "9182|Status"
   ```

1. 您应该会看到类似以下内容的输出，其中AC-9182返回&#x200B;*已应用*&#x200B;状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/AC-9182_USPS_Ground_Advantage_shipping_method_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```
