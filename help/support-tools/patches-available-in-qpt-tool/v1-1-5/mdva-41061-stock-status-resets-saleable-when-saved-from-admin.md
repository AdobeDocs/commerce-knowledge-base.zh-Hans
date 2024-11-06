---
title: 'MDVA-41061：从管理员保存产品时，库存状态将重置为可销售'
description: MDVA-41061修补程序修复了在从管理员保存产品时，库存状态重置为可销售的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41061。 QPT 1.1.15中提供了最新的修补程序版本，带有MDVA-41061-V3修补程序ID。 请注意，Adobe Commerce 2.4.4中已修复该问题。
exl-id: fd71d3e5-685f-4987-b7e7-bfd86810d865
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-41061：从管理员保存产品时，库存状态将重置为可销售

MDVA-41061修补程序修复了在从管理员保存产品时，库存状态重置为可销售的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41061。 QPT 1.1.15中提供了最新的修补程序版本，带有MDVA-41061-V3修补程序ID。 请注意，Adobe Commerce 2.4.4中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.2-p2、2.4.3 - 2.4.3-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从管理员保存产品后，库存状态将重置为可销售。

<u>先决条件</u>：

清单模块已安装。

<u>重现步骤</u>：

1. 创建数量= 1的简单产品。
1. 使用在第1步中创建的产品下订单。
1. 运行cron — 确保已执行`inventory.reservations.updateSalabilityStatus`队列，并且`cataloginventory_stock_status`表中的产品库存状态已更改为零。
1. 检查前端产品。 它应标记为&#x200B;**缺货**。
1. 将产品保存在管理员中，不做任何更改。

<u>预期的结果</u>：

* 库存状态不应更新。
* 前端产品应为&#x200B;**缺货**。

<u>实际结果</u>：

* 简单产品在前端标记为&#x200B;**In Stock**。
* 用户收到&#x200B;*请求的数量不可用*&#x200B;消息（在尝试将其添加到购物车时）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
