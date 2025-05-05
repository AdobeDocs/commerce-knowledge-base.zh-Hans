---
title: “MDVA-42520：使用“启用跨境贸易”时应用两次的税率”
description: MDVA-42520修补程序修复了在使用**启用跨境贸易**时两次应用税率的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11后，即可使用此修补程序。 修补程序ID为MDVA-42520。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520：使用“启用跨境贸易”时应用两次的税率

MDVA-42520修补程序修复了在使用&#x200B;**启用跨境贸易**&#x200B;时两次应用税率的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11时，此修补程序可用。 修补程序ID为MDVA-42520。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用&#x200B;**启用跨境贸易**&#x200B;时，该税率应用两次。

<u>重现步骤</u>：

1. 启用&#x200B;**公司**、**共享目录**&#x200B;和&#x200B;**报价**
1. 根据屏幕截图配置税金。 确保启用&#x200B;**跨境贸易**。

   ![税务设置](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. 为德国创建税率(10%)。
1. 创建税则以应用税率。
1. 创建公司和自定义共享目录。
1. 创建价格为100的产品，并将其包含在自定义共享目录中，且价格折扣为20%。
1. 创建具有德国地址的客户并将其分配给公司
1. 将10个产品作为客户添加到卡。
1. 转到购物车并请求报价。
1. 在后端打开此报价并尝试添加额外的10%折扣。

<u>预期的结果</u>：

报价小计（含税）和报价总计（含税）= $720

<u>实际结果</u>：

报价小计（含税）和报价总计（含税）= $649.50。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
