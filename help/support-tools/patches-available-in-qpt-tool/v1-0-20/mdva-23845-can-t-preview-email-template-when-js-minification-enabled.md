---
title: “MDVA-23845：启用JS缩小后无法预览电子邮件模板”
description: 启用JS缩小后，MDVA-23845Magento修补程序无法在管理员中预览电子邮件模板，从而修复了此问题。
exl-id: 08579251-a0aa-4e84-9d6a-3fa2999d9c05
feature: Communications, Marketing Tools
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# MDVA-23845：启用JS缩小后无法预览电子邮件模板

启用JS缩小后，MDVA-23845Magento修补程序无法在管理员中预览电子邮件模板，从而修复了此问题。

安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20时，此修补程序可用。 修补程序ID为MDVA-23845。 请注意，此问题已在Magento版本2.3.5中修复。

## 受影响的产品和版本

**为Magento版本** Magento Commerce Cloud2.3.3创建修补程序

**与Magento版本兼容：** Magento Commerce和磁控Commerce Cloud2.3.2-2.3.4-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现问题的步骤</u> ：

1. 在&#x200B;**管理员>商店>配置> JavaScript设置>缩小JavaScript文件**&#x200B;中启用&#x200B;**JS缩小** = *是* 。
1. 将Magento切换到生产模式。
1. 转到&#x200B;**管理员>营销>通信>电子邮件模板** 。
1. 单击&#x200B;**添加新模板** 。
1. 选择&#x200B;**新订单**&#x200B;模板。
1. 单击&#x200B;**加载模板**&#x200B;按钮。
1. 用&#x200B;**新订单填充**&#x200B;模板名称&#x200B;**。**
1. 单击&#x200B;**保存模板**&#x200B;按钮。
1. 在电子邮件模板网格中，单击&#x200B;**操作**&#x200B;列中的&#x200B;**预览**&#x200B;链接。

<u>预期的结果</u> ：

电子邮件模板预览会按预期显示在打开的弹出窗口中。

<u>实际结果</u> ：

电子邮件模板预览未出现在打开的弹出窗口中。 弹出窗口为空，可能会出现JS错误。

## 应用修补程序

要应用单独的修补程序，请根据您的Magento产品使用以下链接：

* Magento Commerce： DevDocs [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html) 。
* Magento Commerce Cloud： DevDocs [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 。
* [使用Quality Patches Tool检查Magento问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
