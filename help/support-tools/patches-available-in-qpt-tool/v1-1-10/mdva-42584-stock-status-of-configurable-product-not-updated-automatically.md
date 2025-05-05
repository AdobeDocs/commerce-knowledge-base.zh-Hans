---
title: 'MDVA-42584：可配置产品的库存状态未自动更新'
description: MDVA-42584修补程序解决了在简单产品更新时，可配置产品的库存状态未自动更新的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10后，即可使用此修补程序。 修补程序ID为MDVA-42584。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584：可配置产品的库存状态未自动更新

MDVA-42584修补程序解决了在简单产品更新时，可配置产品的库存状态未自动更新的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10时，此修补程序可用。 修补程序ID为MDVA-42584。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当其简单产品通过API或导入设置为&#x200B;**库存**&#x200B;时，后端中可配置产品的库存状态不会自动更新。

<u>先决条件</u>：

已安装MSI。

<u>重现步骤</u>：

1. 创建可配置的产品&#x200B;**InvCheck001**，它有两个选项：**InvCheck001-M**&#x200B;和&#x200B;**InvCheck001-L**。
1. 简单产品都应该具有数量，并且它们应该是&#x200B;**库存**，这样可配置产品在后端也是&#x200B;**库存**。
1. 现在，更新简单产品并将数量设置为&#x200B;**0**，库存状态设置为&#x200B;**缺货**。
1. 刷新可配置产品并验证库存状态是否更新为&#x200B;**缺货**。
1. 使用以下API终结点，并将简单产品&#x200B;**InvCheck001-M**&#x200B;设置为&#x200B;**Stock**&#x200B;中的数量> 0。

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. 转到后端并验证简单产品&#x200B;**InvCheck001-M**&#x200B;的数量和库存状态。 已更新为&#x200B;**库存**。
1. 刷新可配置产品并检查库存状态。

<u>预期的结果</u>：

后端中可配置产品&#x200B;**InvCheck001**&#x200B;的库存状态自动更新为&#x200B;**In Stock**。

<u>实际结果</u>：

可配置产品的库存状态仍为&#x200B;**缺货**。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
