---
title: 'MDVA-31224修补程序：产品价格重新指数耗时过长'
description: MDVA-31224修补程序解决了产品价格重新指数需要很长时间才能完成或永远不会完成的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7后，即可使用此修补程序。
exl-id: 17f83fbf-9a43-4a65-b560-5f729b037c17
feature: Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# MDVA-31224修补程序：产品价格重新指数耗时过长

MDVA-31224修补程序解决了产品价格重新指数需要很长时间才能完成或永远不会完成的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.7时，此修补程序可用。

## 受影响的产品和版本

* 该补丁是为Cloud Infrastructure 2.3.3上的Adobe Commerce设计的。
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.3 - 2.3.4-p2上的Adobe Commerce。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品价格重新指数需要很长时间才能完成，或者永远不会完成。

<u>要再现的步骤：</u>

1. 创建包含15个选项的6000个捆绑产品。
1. 创建包含30个选项的1个捆绑产品。
1. 从CLI运行价格重新索引：     `bin/magento indexer:reindex catalog_product_price`

<u>预期结果：</u>

完成产品价格重新索引需要1.5小时或更长时间。

<u>实际结果：</u>

产品价格重新索引需要很短时间（一两分钟）才能完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
