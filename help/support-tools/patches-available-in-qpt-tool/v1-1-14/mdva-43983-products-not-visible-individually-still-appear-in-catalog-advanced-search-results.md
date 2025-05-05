---
title: 'MDVA-43983：设置为“单独不可见”的产品将显示在搜索结果中'
description: MDVA-43983修补程序解决了设置为“不可见”的产品仍然显示在目录高级搜索结果中的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43983。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 2599fb6c-5b27-461b-9740-f586ae7df9f5
feature: Catalog Management, Products, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-43983：设置为“单独不可见”的产品将显示在搜索结果中

MDVA-43983修补程序解决了设置为“不可见”的产品仍然显示在目录高级搜索结果中的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-43983。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

设置为“单独不可见”的产品仍会显示在目录高级搜索结果中。

<u>重现步骤</u>：

1. 为存储区所有者&#x200B;**创建具有**&#x200B;目录输入类型的属性作为&#x200B;**下拉列表**&#x200B;或&#x200B;**可视化样本**（例如，颜色）。
1. 将&#x200B;**在搜索中使用**&#x200B;设置为&#x200B;**是**，将&#x200B;**在高级搜索中可见**&#x200B;设置为&#x200B;**是**。
1. 添加一些属性选项。
1. 创建具有&#x200B;**可见性**&#x200B;的产品，因为&#x200B;**不可单独显示**。
1. 指定颜色属性选项。
1. 转到店面上的&#x200B;**目录高级搜索**&#x200B;页面。
1. 从“颜色”属性字段中仅选择“颜色”属性选项，并将其余字段留空或保持原样。
1. 提交高级搜索表单。
1. 观察搜索结果。

<u>预期的结果</u>：

设置为“不可见”的产品不会出现在目录高级搜索结果中。

<u>实际结果</u>：

设置为“单独不可见”的产品将显示在目录高级搜索结果中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
