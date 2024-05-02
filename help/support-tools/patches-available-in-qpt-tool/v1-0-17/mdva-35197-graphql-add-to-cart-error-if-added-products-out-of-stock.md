---
title: 'MDVA-35197：如果添加的产品缺货，则GraphQL添加到购物车出错'
description: MDVA-35197修补程序修复了在使用GraphQL添加到购物车时，如果之前添加的产品缺货，则会出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17后，即可使用此修补程序。
exl-id: 189312f7-a505-4ba4-b12d-662987e69374
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-35197：如果添加的产品缺货，则GraphQL添加到购物车出错

MDVA-35197修补程序修复了在使用GraphQL添加到购物车时，如果之前添加的产品缺货，则会出现错误的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.17。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果购物车中已有的其他产品(也通过GraphQL添加)缺货，则在尝试通过GraphQL将产品添加到购物车时出错。

<u>重现问题的步骤</u>：

1. 使用GraphQL将任何产品添加到购物车。
1. 登录到Commerce管理面板，并将此产品设置为无库存。
1. 尝试通过GraphQL向购物车中添加其他产品。

<u>预期结果</u>：

可以将库存产品添加到购物车。

<u>实际结果</u>：

GraphQL错误消息： *有些产品缺货*. 无法添加新的“现货”产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
