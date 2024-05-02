---
title: 'MDVA-30428：愿望清单不适用于Inventory management'
description: MDVA-30428修补程序解决了愿望清单不适用于Inventory management (MSI)的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5后，即可使用此修补程序。
exl-id: 79e8d5d6-b073-48cf-8ecc-5c44667c12ad
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-30428：愿望清单不适用于Inventory management

MDVA-30428修补程序解决了愿望清单不适用于Inventory management (MSI)的问题。 此修补程序在以下情况下可用： [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 已安装1.0.5。

## 受影响的产品和版本

**该修补程序是为Adobe Commerce版本创建的：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.3 - 2.3.3-p1 (QPT 1.0.6)和2.3.5 - 2.4.1 (QPT 1.0.5)

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查该修补程序是否与您的Adobe Commerce版本兼容，请更新 `magento/quality-patches` 包到最新版本，并检查 [[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在将产品添加到愿望清单时，当该产品被分配给自定义库存来源时，以下消息显示“*我们现在无法将项目添加到愿望清单：无法将没有库存的产品添加到愿望清单。*&quot;

<u>重现问题的步骤</u>：

1. 在Commerce管理中创建新清单来源。 有关步骤，请参阅 [目录>添加新源](https://docs.magento.com/user-guide/catalog/inventory-sources-add.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=new%20inventory%20source) 在我们的用户指南中。
1. 在Commerce管理员中创建新库存清单，将新来源和默认网站分配给新库存。 有关步骤，请参阅 [“目录”>“添加新库存”](https://docs.magento.com/user-guide/catalog/inventory-stock-add.html#add-new-stock) 在我们的用户指南中。
1. 创建一个简单的产品，并仅将新库存分配为库存。
1. 访问前端中的简单产品详细信息页面。
1. 将产品添加到愿望清单。 以下错误显示： *我们现在无法将项目添加到愿望清单：无法将没有库存的产品添加到愿望清单*.

<u>预期结果</u>：

产品应添加到具有自定义股票的愿望清单中。

<u>实际结果</u>：

产品未添加到愿望清单，并显示一条错误消息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用补丁程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) 在我们的开发人员文档中。
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html) 在我们的开发人员文档中。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 在我们的支持知识库中。
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) 在我们的支持知识库中。

有关QPT中可用的其他修补程序的信息，请参阅 [QPT中可用的修补程序](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) 在我们的开发人员文档中。
