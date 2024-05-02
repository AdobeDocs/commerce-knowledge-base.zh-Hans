---
title: 'MDVA-30845：签出中断与装运提供商的连接失败'
description: MDVA-30845修补程序修复了以下问题：在签出期间无法连接到UPS XML/USPS/DHL，并且没有其他送货方法可用时，显示*抱歉，此订单目前没有引号可用*错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.2中修复。
exl-id: 7be54213-1762-431b-bd3b-080c3d45f492
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-30845：签出中断与装运提供商的连接失败

MDVA-30845修补程序修复了 *抱歉，目前此订单没有报价* 在签出期间无法连接到UPS XML/USPS/DHL时显示错误，并且没有其他送货方法可用。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.12。 请注意，该问题计划在Adobe Commerce 2.4.2中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：** 云基础架构上的Adobe Commerce 2.3.5-p2.

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.5-2.3.6。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在结账过程中， *抱歉，目前此订单没有报价* 无法连接到UPS XML/USPS/DHL时显示错误，并且没有其他送货方法可用。

<u>重现问题的步骤：</u>

1. 创建产品。
1. 启用和配置UPS XML发运方法。
1. 将产品添加到商店前面的购物车。
1. 确保提供UPS配送方式和统一费率配送。
1. 编辑主机文件，以防止USP连接到其网关。
1. 在商店前面，尝试获取费率，然后再次进行结账。

<u>实际结果：</u>

*抱歉，目前此订单没有报价* 显示错误，并且无法使用统一费率运输。

<u>预期结果：</u>

未显示错误消息并且提供统一费率送货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。


## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
