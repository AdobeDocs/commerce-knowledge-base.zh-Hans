---
title: 'MDVA-31168修补程序：产品导出文件未显示在管理员中'
description: MDVA-31168修补程序解决了产品导出CSV文件未出现在可导出CSV文件列表中的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.2中已修复此问题。
exl-id: 780a926b-2aea-47c2-8f95-907cc779bfa4
feature: Admin Workspace, Categories, Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# MDVA-31168修补程序：产品导出文件未显示在管理员中

MDVA-31168修补程序解决了产品导出CSV文件未出现在可导出CSV文件列表中的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10时，此修补程序可用。 请注意，Adobe Commerce版本2.4.2中已修复此问题。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本** Adobe Commerce内部部署2.3.5-p2创建的。

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.0 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

使用示例数据安装Adobe Commerce。

<u>要再现的步骤：</u>

1. 创建可下载的产品，并将其分配给&#x200B;**包**&#x200B;类别。
1. 启动所有产品的导出。
1. 从CLI运行以下命令：    ```php    bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000    ```

<u>预期结果：</u>

包含所有产品的产品导出CSV文件会按预期显示在管理员的文件列表中。

<u>实际结果：</u>

包含所有产品的产品导出CSV文件不会显示在管理员的列表中，但只包含标题的文件将在服务器的`/var`文件夹中生成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
