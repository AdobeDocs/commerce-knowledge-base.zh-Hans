---
title: 'MDVA-28661：更改管理员电子邮件时出现公司用户管理问题'
description: MDVA-28861修补程序修复了用户在更改管理员电子邮件时出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。 修补程序ID为MDVA-28861。
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661：更改管理员电子邮件时出现公司用户管理问题

MDVA-28861修补程序修复了用户在更改管理员电子邮件时出现错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5时，此修补程序可用。 修补程序ID为MDVA-28861。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0到2.4.1（包括2.3.5-p1）以及B2B扩展

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

更改&#x200B;**公司管理员**&#x200B;电子邮件地址后，返回了一个错误，并且未显示&#x200B;**公司用户**&#x200B;列表。

<u>重现步骤</u>：

1. 启用公司功能(在[安装B2B中了解详细信息：在开发人员文档的“Commerce管理员”中启用B2B功能](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin)，并创建一个包含两个用户（一个管理员和两个用户）的新公司，所有用户均具有电子邮件地址)。
1. 转到&#x200B;**Commerce管理员** > **客户** > **公司**，并打开您的公司帐户。
1. 打开&#x200B;**公司管理员**&#x200B;选项卡并将管理员更改为第一个用户，其中包括将&#x200B;**公司管理员**&#x200B;电子邮件更改为第一个用户的电子邮件。
1. 前往Adobe Commerce前端，并以第一个用户身份登录。
1. 转到&#x200B;**公司用户**&#x200B;部分。

<u>预期的结果</u>：

**公司用户**&#x200B;列表应按预期显示。

<u>实际结果</u>：

未显示&#x200B;**公司用户**&#x200B;列表，并且显示类似于以下内容的错误：

```bash
No such entity with id = 2
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。

要了解有关B2B公司功能的更多信息，请参阅我们的开发人员文档中的以下文章：

* [B2B开发人员指南](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [管理公司角色](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Adobe Commerce Enterprise B2B扩展配置路径参考](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
