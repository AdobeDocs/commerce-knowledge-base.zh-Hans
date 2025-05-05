---
title: 'MDVA-41350：当管理员将产品添加到其访问权限之外时会出现异常'
description: MDVA-41350修补程序修复了在管理员用户按其访问范围以外的SKU的顺序添加产品时引发异常错误而不是限制访问通知的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11后，即可使用此修补程序。 修补程序ID为MDVA-41350。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 3a96d029-5350-4dd6-aad3-2f2cdd5e65ac
feature: Admin Workspace, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-41350：当管理员将产品添加到其访问权限之外时会出现异常

MDVA-41350修补程序修复了在管理员用户按其访问范围以外的SKU的顺序添加产品时引发异常错误而不是限制访问通知的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11时，此修补程序可用。 修补程序ID为MDVA-41350。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当具有受限访问权限的管理员用户按SKU在订单中超出其访问权限添加产品时，会发生异常，而不是出现消息通知用户其有限访问权限。

<u>重现步骤</u>：

1. 以仅有权访问特定网站的用户身份登录管理员。
1. 转到&#x200B;**销售** > **订单**，然后单击&#x200B;**创建新订单**。
1. 选择客户和商店视图。
1. 单击&#x200B;**按SKU添加产品**。
1. 搜索未分配给任何网站或未分配给您有权访问的网站的SKU。
1. 单击&#x200B;**添加至订单**。

<u>预期的结果</u>：

将显示相应的错误消息。

<u>实际结果</u>：

出现异常。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
