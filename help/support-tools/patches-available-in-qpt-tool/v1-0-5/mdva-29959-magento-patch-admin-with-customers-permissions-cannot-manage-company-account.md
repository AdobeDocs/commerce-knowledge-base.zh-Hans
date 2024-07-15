---
title: 'MDVA-29959修补程序：具有“客户”权限的管理员无法管理公司帐户'
description: '[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版中提供的MDVA-29959修补程序修复了具有“客户”ACL所有权限的受限制管理员用户无法管理公司（添加或删除公司）的问题。 请注意，已在Adobe Commerce 2.3.4的B2B中修复此问题。'
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# MDVA-29959修补程序：具有“客户”权限的管理员无法管理公司帐户

[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)工具1.0.5版中提供的MDVA-29959修补程序修复了具有“客户”ACL所有权限的受限制管理员用户无法管理公司（添加或删除公司）的问题。 请注意，已在Adobe Commerce 2.3.4的B2B中修复此问题。

## 受影响的产品和版本

云基础架构上的Adobe Commerce的B2B 2.3.0-2.3.3-p1.

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有“客户”ACL所有权限的管理员用户无法管理公司（添加或删除公司）。

<u>重现步骤</u>

1. 在Commerce管理员中，创建新管理员角色，并将用户分配给该角色。
1. 仅将“客户”资源分配给角色。
1. 以具有此角色的用户身份登录。
1. 尝试删除公司帐户。

<u>预期结果：</u>

已成功删除公司帐户。

<u>实际结果：</u>

您无法删除公司帐户。 您获得&#x200B;*对不起，您需要权限才能查看此内容。*&#x200B;错误消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
