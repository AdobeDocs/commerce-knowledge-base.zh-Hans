---
title: 'MC-42528：categoryList的GraphQL查询显示所有类别'
description: MC-42528修补程序解决了以下问题：当特定类别的浏览类别设置为“拒绝”时，“categoryList”的GraphQL查询会返回已分配和未分配的类别。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4后，即可使用此修补程序。 修补程序ID为MC-42528。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 8bb29f43-92ae-4f37-b147-7121b55c185b
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MC-42528：categoryList的GraphQL查询显示所有类别

MC-42528修补程序解决了当特定类别的浏览类别设置为“拒绝”时，`categoryList`的GraphQL查询返回已分配和未分配类别的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.4时，此修补程序可用。 修补程序ID为MC-42528。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`categoryList`的GraphQL查询返回已分配和未分配的类别。

<u>重现步骤</u>：

1. 创建两个类别：CAT1和CAT2，并为每个类别分配少量产品。
1. 创建专用共享目录。
1. 创建公司用户并将其分配给创建的共享目录。
1. 将CAT1分配给自定义目录，并将专用目录的客户组的类别权限设置为“允许”浏览类别。
1. 将CAT2的类别权限设置为“拒绝”浏览类别，以访问私有目录的客户组。
1. 以公司用户身份运行`categoryList`或`categories` GraphQL查询。

<u>预期的结果</u>：

响应中只显示CAT1。

<u>实际结果</u>：

所有类别都会显示在响应中，无论类别的浏览权限如何。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修补程序部分。
