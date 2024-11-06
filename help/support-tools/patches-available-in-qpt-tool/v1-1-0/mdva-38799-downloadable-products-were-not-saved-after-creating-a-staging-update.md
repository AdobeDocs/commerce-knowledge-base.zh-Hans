---
title: 'MDVA-38799：创建暂存更新后未保存可下载的产品'
description: MDVA-38799修补程序解决了创建暂存更新后无法保存可下载产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-38799。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799：创建暂存更新后未保存可下载的产品

MDVA-38799修补程序解决了创建暂存更新后无法保存可下载产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0时，此修补程序可用。 修补程序ID为MDVA-38799。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

创建暂存更新后未保存可下载的产品。 用户收到错误消息： *可下载的示例与产品无关。 请验证链接并重试*。

<u>重现步骤</u>：

1. 导航到&#x200B;**目录** > **产品**。
1. 单击“Add Product（添加产品）”旁边的下拉菜单并选择“Downloadable Product（可下载产品）”。
   * 填写产品的名称、SKU、价格和数量。
1. 向下滚动至可下载信息页面。
1. 在示例下，单击&#x200B;**添加链接**。
   * 填写标题、上传文件（文件类型无关紧要）。
1. 单击&#x200B;**保存**。 您会收到以下消息：*您保存了产品*。
1. 单击页面顶部的&#x200B;**计划新更新**。
   * 填写更新名称以及合法的开始日期和结束日期。
1. 在暂存更新中单击&#x200B;**保存**。
1. 单击产品上的&#x200B;**保存**。

<u>预期的结果</u>：

保存产品时不会出现任何错误。

<u>实际结果</u>：

您收到错误消息： *可下载的示例与产品无关。 请验证链接并重试*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
