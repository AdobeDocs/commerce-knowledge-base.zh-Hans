---
title: 'MDVA-41164：无法保存或编辑具有自定义客户属性的公司'
description: MDVA-41164修补程序解决了管理员用户无法保存或编辑具有任何类型的文件或图像的自定义客户属性的公司的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41164。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164：无法保存或编辑具有自定义客户属性的公司

MDVA-41164修补程序解决了管理员用户无法保存或编辑具有任何类型的文件或图像的自定义客户属性的公司的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41164。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员用户无法通过任何类型的文件或图像的自定义客户属性保存或编辑公司。

<u>先决条件</u>：

B2B模块已安装。

<u>重现步骤</u>：

1. 在&#x200B;**商店** > **配置** > **B2B功能**&#x200B;中启用公司。
1. 在&#x200B;**商店** > **属性** > **客户** > **添加新属性**&#x200B;中创建客户属性：
   * 输入类型：文件（附件）
   * 在店面显示：是
   * 排序顺序：任意
   * 要用在中的Forms：全选
1. 在&#x200B;**客户** > **公司** > **添加新公司**&#x200B;中创建新公司，并上载上面创建的新属性的文件。

<u>预期的结果</u>：

用户能够完成公司的创建，并且附件上传无任何错误。

<u>实际结果</u>：

* 您收到错误消息： *保存文件时出错。*
* 异常日志包含如下记录：

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
