---
title: 升级到v10 DHL模式以继续提供DHL运输
description: 本文提供了一个解决方案，通过升级到模式10.0或应用AC-3023修补程序，允许商家在2022年12月DHL模式6.2被弃用后继续提供DHL交付。
exl-id: eed83713-2d6a-4360-bfa1-bebd4d604f2f
feature: Orders, Shipping/Delivery, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# 升级到10.0版DHL模式以继续提供DHL装运

本文提供了一个解决方案，以允许商家在DHL架构版本6.2于2022年12月底被弃用后继续提供DHL配送。

## 受影响的产品和版本

* Adobe Commerce 2.4.5及更早版本、所有部署方法。

## 问题

2022年8月，我们发布了 [DHL架构版本6.2的升级，以及修复修补程序](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) 商户继续提供DHL运输。 DHL将于2022年10月再次引入较新的模式（版本10.0），之前的版本（6.2模式）将于2022年12月底弃用。 Adobe Commerce 2.4.5及更早版本的DHL集成仅支持版本6.2。

## 解决方案

2022年10月发布的Adobe Commerce 2.4.5-p1和2.4.4-p2包含新的DHL模式版本10.0。因此，升级到2.4.5-p1和2.4.4-p2的商家无需采取任何操作即可继续提供DHL托运。 我们鼓励所有商家在2022年12月底弃用DHL模式6.2之前升级到2.4.5-p1和2.4.4-p2。

如果商户不希望升级到2.4.5-p1和2.4.4-p2，并且希望在2022年12月之后继续提供DHL传送，则需要应用修复补丁程序。

## Patch

修补程序ID为AC-3023，可在 [!DNL Quality Patches Tool] 版本1.1.21。

请参阅以下链接，了解如何使用 [!DNL Quality Patches Tool] 和安装修补程序，具体取决于您的部署方法：

* Adobe Commerce内部部署和Magento Open Source： [Quality Patches Tools > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 在Adobe Experience League中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

**该修补程序适用于以下Adobe Commerce版本（所有部署方法）：**

* 2.3.7、2.4.0、2.4.1、2.4.2、2.4.3、2.4.3-p2、2.4.3-p3、2.4.4

## 有用的链接

* [[!DNL Quality Patches Tool] >发行说明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) 在Adobe Experience League中。

* [[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 在Adobe Experience League中。

## 相关阅读

* [应用修补程序以继续将DHL作为运输运营商](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/adobe-commerce-dhl-upgrade-patch.html) 在我们的支持知识库中。

* [装运承运人> DHL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/shipping-carriers/dhl.html) 在我们的用户指南中。
* [配置参考>销售>交付方法](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/delivery-methods.html) 在我们的用户指南中。
