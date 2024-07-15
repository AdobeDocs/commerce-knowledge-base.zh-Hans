---
title: 'MDVA-30858：缺少PayPal结算报告'
description: “MDVA-30858修补程序修复了在拥有多个PayPal帐户时缺少PayPal结算报告的问题。 这些报告应位于管理员侧栏&amp；**Reports**&amp；gt； Sales &amp；gt； **PayPal Settlement**下。 而是显示消息： *我们找不到任何记录。*显示。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。”
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858：缺少PayPal结算报告

MDVA-30858修补程序修复了在拥有多个PayPal帐户时缺少PayPal结算报告的问题。 这些报告应位于管理员侧栏> **报告** >销售> **PayPal结算**&#x200B;下。 而是消息：*我们找不到任何记录。显示*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.4

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了在拥有多个PayPal帐户时，在&#x200B;**报表** > Sales > **PayPal结算**&#x200B;中未找到记录的问题。

<u>重现步骤</u>：

1. 配置PayPal结算报表。
1. 转到管理员，转到&#x200B;**报表** >销售> **PayPal结算**。
1. 有关最新更新，请单击右上角的&#x200B;**获取更新**。

<u>预期的结果</u>：

此时应会显示报表。

<u>实际结果</u>：

网格中不会显示任何内容，但报表可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
