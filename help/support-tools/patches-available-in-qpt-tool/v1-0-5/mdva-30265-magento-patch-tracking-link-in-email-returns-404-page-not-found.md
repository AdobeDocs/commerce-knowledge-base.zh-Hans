---
title: 'MDVA-30265：电子邮件中的跟踪链接返回404页面未找到'
description: MDVA-30265修补程序解决了客户单击订单确认电子邮件中的发运跟踪链接时，出现“404页面未找到”错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265：电子邮件中的跟踪链接返回404未找到页面

MDVA-30265修补程序解决了客户单击订单确认电子邮件中的发运跟踪链接时，出现“404页面未找到”错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.3到2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在为下订单创建发运后，会向客户发送一封电子邮件，其中包含跟踪信息和用于跟踪订单的链接。 但是，当客户单击电子邮件中的装运跟踪链接时，这会返回“404页面未找到”错误。

<u>重现步骤</u>：

1. 安装Adobe Commerce 2.4。有关步骤，请参阅我们的开发人员文档中的[使用编辑器安装Adobe Commerce](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html)。
1. 下订单。
1. 转到“管理”面板> **销售** > **订单**。 查找您刚刚创建的订单并将其打开。
1. 创建发运并添加跟踪编号（承运人=自定义值）。 有关步骤，请参阅我们的用户指南中的[Order Management >创建装运](https://docs.magento.com/user-guide/sales/shipments-create.html)。
1. 您会收到一封电子邮件。 单击跟踪链接以检查它是否正常工作。
1. 创建发票。 有关步骤，请参阅我们的用户指南中的[Order Management >创建发票](https://docs.magento.com/user-guide/sales/invoice-create.html)。 然后，再次单击上面的跟踪链接。

<u>预期的结果</u>：

即使在创建发票后，跟踪链接也应有效。

<u>实际结果</u>：

创建发票后，跟踪链接不起作用并返回“404页面未找到”错误页。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
