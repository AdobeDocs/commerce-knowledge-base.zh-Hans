---
title: 'MDVA-36464：发送在商店视图级别不工作的电子邮件设置'
description: MDVA-36464修补程序修复了在商店视图级别发送电子邮件设置不起作用的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21后，即可使用此修补程序。 修补程序ID为MDVA-36464。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: cdf7e208-90ee-4711-8407-026da42fe3c8
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# MDVA-36464：发送在商店视图级别不工作的电子邮件设置

MDVA-36464修补程序修复了在商店视图级别发送电子邮件设置不起作用的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21时，此修补程序可用。 修补程序ID为MDVA-36464。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件：</u>

安装干净的Adobe Commerce。

<u>重现步骤</u>：

1. 创建其他网站、商店和商店视图（在此示例中，第二个网站是&#x200B;*website2*）。
1. 在&#x200B;**商店** > **配置** > **高级** > **系统** > **邮件发送设置**&#x200B;中的全局级别上禁用&#x200B;**电子邮件通知**。
1. 在&#x200B;*网站2*&#x200B;级别上启用&#x200B;**电子邮件通知** （**禁用电子邮件通信** = *否*）。
1. 在“管理员”中，创建一个新用户，并将其分配给&#x200B;*网站2*。
1. 在“管理员”中，在客户编辑页面上，单击上面在步骤4中创建的客户的&#x200B;**重置密码**。

<u>预期的结果</u>：

**欢迎电子邮件**&#x200B;和&#x200B;**重置密码电子邮件**&#x200B;均按预期发送，因为&#x200B;**禁用第二个网站的电子邮件通信** = *否*（示例： *网站2*）。

<u>实际结果</u>：

* 未触发创建新客户后的&#x200B;**欢迎电子邮件**。
* 未触发&#x200B;**重置密码电子邮件**。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
