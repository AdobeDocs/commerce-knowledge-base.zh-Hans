---
title: 'MDVA-23426Magento修补程序：作为附件从Outlook发送的电子邮件'
description: MDVA-23426Magento修补程序修复了通过MS Outlook中的Magento将电子邮件作为附件发送的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。 请注意，已在Magento2.3.5中修复此问题。
exl-id: 0b4c3e33-76c5-48b0-b1a8-a967cea11b98
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# MDVA-23426Magento修补程序：作为附件从Outlook发送的电子邮件

MDVA-23426Magento修补程序修复了通过MS Outlook中的Magento将电子邮件作为附件发送的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13后，即可使用此修补程序。 请注意，已在Magento2.3.5中修复此问题。

## 受影响的产品和版本

**为Magento版本** Magento Commerce Cloud2.3.3创建修补程序。

**与Magento版本兼容：** Magento Commerce和Magento Commerce Cloud2.3.3 - 2.3.4-p2。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

接收带有空白正文的电子邮件，内容将作为附件包含在内。

<u>先决条件： </u> Outlook/Exchange正在用作客户端/服务器组合。

<u>要再现的步骤：</u> 1. 提交订单，订单通知或发运通知已发送。2.已收到电子邮件。

<u>实际结果：</u>电子邮件显示空白正文，内容作为ATT\*标记的附件包含在电子邮件中。 <u>预期结果：</u>

接收电子邮件时没有附件，电子邮件的正文包含内容。

## 应用修补程序

有关如何应用QPT补丁程序的说明，请根据您的Magento产品使用以下链接：

* Magento Commerce： DevDocs [使用Quality Patches Tool](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)应用修补程序。
* Magento Commerce Cloud： DevDocs [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 。
* [使用Quality Patches Tool检查Magento问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
