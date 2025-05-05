---
title: 'MDVA-39923：在B2B快速订购功能中按SKU搜索区分大小写'
description: MDVA-39923修补程序修复了以下问题：当客户在B2B快速订购功能中按SKU搜索订单（大小写与保存名称的大小写不同）时，会出现错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39923。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923：在B2B快速订购功能中按SKU搜索区分大小写

MDVA-39923修补程序修复了以下问题：当客户在B2B快速订购功能中按SKU搜索订单（大小写与保存名称的大小写不同）时，会出现错误。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39923。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在B2B快速订购功能中通过SKU搜索是区分大小写的，当使用与保存SKU的大小写不同的大小写时，会显示错误。

<u>先决条件</u>：

已安装B2B模块。

<u>重现步骤</u>：

1. 登录到管理员并转到&#x200B;**商店** > **配置** > **B2B**。
1. 启用&#x200B;**共享目录**&#x200B;和&#x200B;**快速订购**。
1. 创建具有大写SKU的产品，例如TEST20-1234
1. 将创建的产品分配给&#x200B;**共享目录**。
1. 以客户身份登录，然后单击&#x200B;**快速订购**。
1. 以小写形式输入SKU，例如test20-1234。

<u>预期的结果</u>：

无论使用何种箱子，都应找到产品。

<u>实际结果</u>：

收到以下错误消息： *1个产品需要您注意*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
