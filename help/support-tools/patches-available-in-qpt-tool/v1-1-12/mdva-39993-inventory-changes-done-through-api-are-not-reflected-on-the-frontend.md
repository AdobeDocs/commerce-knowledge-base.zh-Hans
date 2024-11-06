---
title: 'MDVA-39993：通过API完成的库存更改未反映在店面上'
description: MDVA-39993修补程序解决了通过API完成的清单更改未反映在店面中的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-39993。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993：通过API完成的库存更改未反映在店面上

MDVA-39993修补程序解决了通过API完成的清单更改未反映在店面中的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-39993。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.3.7-p2和2.4.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过API完成的库存更改不会反映在店面产品页面上。

<u>先决条件</u>：

已安装清单模块。

<u>重现步骤</u>：

1. 确保队列设置为在cron安装并运行的情况下执行，并且cron已安装和运行。
1. 创建具有两种颜色（黑色和红色）以及两种尺寸（M和L）的可配置产品(COC001)。
1. 选择无库存(COC001-Red-M)。
1. 在店面中加载可配置的产品页面，然后尝试单击每个颜色。 当您单击&#x200B;**红色**&#x200B;时，应该取消大小&#x200B;**M**，因为它没有库存。
1. 使用以下API端点和有效负载生成COC001-Red-M备货：

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. 从后端检查此简单产品，验证它是否已更新为有货。
1. 从前端加载可配置产品，然后单击每个颜色。 单击&#x200B;**红色**&#x200B;时，请注意大小&#x200B;**M**。

<u>预期的结果</u>：

没有划出COC001-Red-M选项，因为我们已经通过API将其更新为库存。

<u>实际结果</u>：

COC001-Red-M期权仍被剔除，尽管它有存货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
