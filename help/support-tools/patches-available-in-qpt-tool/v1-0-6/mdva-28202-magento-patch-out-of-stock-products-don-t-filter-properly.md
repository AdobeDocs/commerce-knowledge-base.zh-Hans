---
title: “MDVA-28202修补程序：缺货产品未正确过滤”
description: MDVA-28202修补程序解决了在Adobe Commerce商店前端使用**Price**过滤器未正确过滤缺货产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6后，即可使用此修补程序。
exl-id: 45976602-15f3-4fef-9d90-da2b3fe6046d
feature: Catalog Management, Categories, Orders, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-28202修补程序：缺货产品未正确过滤

MDVA-28202修补程序解决了在Adobe Commerce商店前端使用&#x200B;**Price**&#x200B;过滤器未正确过滤缺货产品的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) v.1.0.6时，此修补程序可用。

## 受影响的产品和版本

* 该补丁是为Cloud Infrastructure 2.3.5-p1上的Adobe Commerce设计的。
* 该补丁还兼容本地Adobe Commerce和Cloud Infrastructure 2.3.4 - 2.4.1上的Adobe Commerce。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

缺货产品在Commerce管理员中使用&#x200B;**价格**&#x200B;筛选器无法正确过滤。

<u>先决条件：</u>

* 在&#x200B;**商店>配置>目录>库存>库存选项**&#x200B;下，设置&#x200B;**显示缺货产品** = &quot;*是*&quot;。

<u>要再现的步骤：</u>

1. 创建包含两个简单产品的可配置产品（例如：设置&#x200B;**价格** = *$1500*）。
1. 创建可配置产品时，两个简单产品都应“缺货”。
1. 将此可配置产品分配给类别。
1. 使用以上可配置产品的实体ID重新索引并检查`catalog_product_index_price`表。
1. 保存所有产品价格= *$0*。
1. 加载类别并确认产品的可用性。
1. 从分层导航中打开&#x200B;**Price**&#x200B;筛选器。
1. 请注意，**价格**&#x200B;筛选器有一个选项“*$0.00 - $9.99*”。
1. 单击上面的&#x200B;**价格**&#x200B;筛选器选项并设置&#x200B;**价格** = *$1500*，您将获得我们上面创建的可配置产品。

<u>预期结果：</u>

产品会按预期筛选在正确价格范围下的产品。

<u>实际结果：</u>

产品属于错误的价格范围过滤器。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署：在开发人员文档中[使用Quality Patches Tool](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)应用修补程序。
* 云基础架构上的Adobe Commerce：在开发人员文档中，[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。

要了解有关可配置产品的更多信息，请参阅我们的开发人员文档中的这篇文章： [在开发人员文档中创建一个可配置产品教程](https://devdocs.magento.com/guides/v2.4/rest/tutorials/configurable-product/config-product-intro.html)。
