---
title: 'MDVA-31021：如果产品选项过多，则导入和导出速度缓慢'
description: MDVA-31021修补程序解决了在大量产品选项的情况下，导入/导出时间比预期更长的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。
exl-id: d294b30d-b734-4bd6-bf1a-c116b789a63c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-31021：如果有许多产品选项，则导入和导出速度较慢

MDVA-31021修补程序解决了在大量产品选项的情况下，导入/导出时间比预期更长的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果`catalog_product_option`表中有100,000条或更多的记录，则导入/导出函数文件验证所需的时间会比预期要长。 在导入/导出之前，为了检查选项验证，Adobe Commerce会为所有现有产品加载产品选项。

<u>先决条件</u>：

Adobe Commerce商店提供5000种产品以及自定义选项。 每个产品应至少有四个自定义选项，其中应有两个或多个选项可供选择，以便`catalog_product_option`表中有100,000条记录。

<u>重现步骤</u>：

1. 对于&#x200B;**导入**&#x200B;示例：使用Commerce管理员提供的其中一个SKU创建一个CSV导入文件。
1. 向CSV导入文件中添加四个自定义选项。
1. 尝试从Commerce管理员导入CSV文件。

<u>预期的结果</u>：

导入或导出功能按预期完成。 使用一个产品完成验证只需要不到10秒。

<u>实际结果</u>：

导入或导出函数所需的时间比预期要长。 仅需一个产品即可完成验证，耗时10秒以上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
