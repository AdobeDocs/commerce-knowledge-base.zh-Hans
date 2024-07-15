---
title: “MDVA-32449：销售订单历史记录缓慢或未加载并出现503错误”
description: MDVA-32449修补程序解决了Adobe Commerce上销售订单历史记录加载缓慢或不加载并显示503错误的问题。 当将13000+个客户分配到B2B公司时，会出现此问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。 请注意，此问题已在Adobe Commerce 2.4.1中修复。
exl-id: e3fd4db2-b706-4712-ba8e-270eaca7fdb2
feature: B2B, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-32449：销售订单历史记录慢或不加载，出现503错误

MDVA-32449修补程序解决了Adobe Commerce上销售订单历史记录加载缓慢或不加载并显示503错误的问题。 当将13000+个客户分配到B2B公司时，会出现此问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12后，即可使用此修补程序。 请注意，此问题已在Adobe Commerce 2.4.1中修复。

## 受影响的产品和版本

当将13000+个客户分配到B2B公司时，会出现此问题。

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.3.5-p2、2.4.0、2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了订单历史记录加载非常缓慢或根本不加载的问题。

<u>先决条件</u>：

分配给B2B公司的13000+个客户

<u>重现步骤</u>：

1. 以公司管理员身份登录到店面。
1. 转至销售订单历史记录页。

<u>预期的结果</u>：

销售订单历史记录页面会正常加载。

<u>实际结果</u>：

页面加载速度非常慢，或者页面可能无法加载并显示超时错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
