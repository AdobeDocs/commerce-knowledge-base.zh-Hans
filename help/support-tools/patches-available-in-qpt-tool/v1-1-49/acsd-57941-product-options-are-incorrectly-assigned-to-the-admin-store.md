---
title: 'ACSD-57941：产品选项未正确分配给管理员商店'
description: Adobe Commerce应用ACSD-57941修补程序以修复以下问题：产品选项被错误地分配给管理员存储区而不是其各自的存储区。广告
feature: Products
role: Admin, Developer
source-git-commit: 1cc673716b75bda6cfe7b3d597ec94e4510fa7e4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-57941：产品选项未正确分配给管理员商店

ACSD-57941修补程序修复了将产品选项错误地分配给管理员存储区而不是其各自存储区的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-57941。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品选项错误地分配给管理员存储而不是其各自的存储。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 使用几个自定义选项导入相同的产品。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;并打开创建的产品。 单击&#x200B;**[!UICONTROL Customizable options]**&#x200B;并确保导入的选项可见。
1. 再次导入同一文件几次。

<u>预期的结果</u>：

自定义选项已更新。

<u>实际结果</u>：

产品自定义选项重复。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。