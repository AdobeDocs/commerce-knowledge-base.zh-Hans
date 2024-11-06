---
title: 'MDVA-43726：对目录价格规则进行部分重新索引后无法应用'
description: MDVA-43726修补程序修复了在部分重新索引后无法应用基于存储级别属性匹配的目录价格规则的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43726。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726：部分重新索引后无法应用目录价格规则

MDVA-43726修补程序修复了在部分重新索引后无法应用基于存储级别属性匹配的目录价格规则的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43726。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在部分重新索引后，无法应用基于存储级别属性匹配的目录价格规则。

<u>重现步骤</u>：

1. 将索引器模式设置为按计划运行。
1. 创建两个可配置的产品属性。 例如：颜色（可视样本）和大小（文本样本）。
1. 使用步骤2中创建的两个属性创建可配置产品。
1. 创建产品后，创建&#x200B;**是/否**&#x200B;类型属性，并使其在规则条件中可见。
1. 将此属性添加到默认属性集。
1. 创建在此属性设置为&#x200B;**是**&#x200B;时要应用的目录价格规则。
1. 打开与可配置产品相关的简单产品之一。
1. 将范围更改为存储视图并将属性值更新为&#x200B;**是**。
1. 运行`CRON`并检查前端价格。
1. 运行完全重新索引。 再次检查前端的价格。
1. 更新可配置产品类别。
1. 运行`CRON`并在前端再次检查价格。

<u>预期的结果</u>：

无需使用增量索引器完全重新索引，目录规则即可正确应用。

<u>实际结果</u>：

如果不运行完整的重新索引，则不会应用目录规则。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
