---
title: “MDVA-37725：通过非默认站点发送的电子邮件包含默认站点的徽标URL”
description: MDVA-37725修补程序修复了以下问题：通过包含默认网站的徽标URL的非默认网站发送异步订单电子邮件。
exl-id: c0d1b9a3-01bb-445b-b7da-f9be6952eaeb
feature: Communications, Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-37725：通过非默认站点发送的电子邮件包含默认站点的徽标URL

>[!WARNING]
>
> 已弃用MDVA-37725修补程序。

MDVA-37725修补程序修复了以下问题：通过包含默认网站的徽标URL的非默认网站发送异步订单电子邮件。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-37725。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

异步订单电子邮件通过包含默认网站徽标URL的非默认网站发送。

<u>先决条件</u>：

1. 必须已创建第二个网站/商店/商店视图。
1. 必须从&#x200B;**商店** > **设置** > **配置** > **销售** > **销售电子邮件** > **常规设置**&#x200B;启用&#x200B;**异步发送**&#x200B;配置。
1. **已打开将商店代码添加到URL**&#x200B;配置，以便从&#x200B;**商店** > **设置** > **配置** > **URL选项**&#x200B;访问辅助网站。

<u>重现步骤</u>：

1. 从第一家和第二家商店下订单。
1. 运行cron以发送销售电子邮件。
1. 检查来自第二个网站的电子邮件。

<u>预期的结果</u>：

电子邮件的徽标URL包含第二个网站的URL。

<u>实际结果</u>：

电子邮件的徽标URL包含默认网站的URL。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的修补程序部分。
