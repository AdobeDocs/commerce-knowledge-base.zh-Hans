---
title: “MDVA-42520：使用“启用跨境贸易”时应用两次的税率”
description: MDVA-42520修补程序修复了在使用**启用跨境贸易**时两次应用税率的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11后，即可使用此修补程序。 修补程序ID为MDVA-42520。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: c1ca44eb-fe92-4f28-807a-3a4563433386
feature: Catalog Management, Orders, Taxes
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-42520：使用“启用跨境贸易”时应用两次的税率

MDVA-42520修补程序修复了以下情况下两次应用税率的问题： **支持跨境贸易** 已使用。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.1.11。 修补程序ID为MDVA-42520。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

倘符合以下条件，则税率适用两次： **支持跨境贸易** 已使用。

<u>重现问题的步骤</u>：

1. 启用 **公司**， **共享目录**、和 **引用**
1. 根据屏幕截图配置税金。 确保启用 **跨境贸易**.

   ![税务设置](/help/support-tools/patches-available-in-qpt-tool/assets/tax_settings_1.png){width="700"}

1. 为德国创建税率(10%)。
1. 创建税则以应用税率。
1. 创建公司和自定义共享目录。
1. 创建价格为100的产品，并将其包含在自定义共享目录中，且价格折扣为20%。
1. 创建具有德国地址的客户并将其分配给公司
1. 将10个产品作为客户添加到卡。
1. 转到购物车并请求报价。
1. 在后端打开此报价并尝试添加额外的10%折扣。

<u>预期结果</u>：

报价小计（含税）和报价总计（含税）= $720

<u>实际结果</u>：

报价小计（含税）和报价总计（含税）= $649.50。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
