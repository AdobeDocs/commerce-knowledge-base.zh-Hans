---
title: 'MDVA-41399：如果客户将产品添加到愿望清单，则无法访问管理购物车'
description: MDVA-41399修补程序解决了当客户将产品添加到愿望清单时，管理员用户无法访问“管理购物车”页面的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.6后，即可使用此修补程序。 修补程序ID为MDVA-41399。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 227653c6-2d20-4475-b973-b9fa58db815b
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-41399：如果客户将产品添加到愿望清单，则无法访问管理购物车

MDVA-41399修补程序解决了当客户将产品添加到愿望清单时，管理员用户无法访问“管理购物车”页面的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.6。 修补程序ID为MDVA-41399。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果客户将产品添加到愿望清单，管理员用户将无法访问“管理购物车”页面。

<u>先决条件</u>：

1. 创建两个或更多产品。
1. 创建客户。
1. 启用开发人员模式。

<u>重现问题的步骤</u>：

1. 前往Storefront并以客户的身份登录，前提条件是：
1. 将产品添加到愿望清单。
1. 转到管理员面板，导航到已创建的客户编辑页面，然后单击 **管理购物车** 按钮。

<u>预期结果</u>：

管理员用户能够管理购物车。

<u>实际结果</u>：

管理员用户收到一条错误消息： *出现错误。 有关详细信息，请参阅错误日志。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) 部分。
