---
title: 'MDVA-44100：所有FPT均已分配给购物车中的最后一个产品'
description: MDVA-44100修补程序解决了将所有FPT分配给购物车中最后一个产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-44100。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: ab0f195c-fcc6-41ac-932d-d2603d068aa6
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-44100：所有FPT均已分配给购物车中的最后一个产品

MDVA-44100修补程序解决了将所有FPT分配给购物车中最后一个产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-44100。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

所有FPT都分配给购物车中的最后一个产品，其余产品的FPT值将被重置。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **配置** > **销售** > **税费**&#x200B;并设置：
   * 启用FPT =是
   * 将税应用于FPT =是
   * 将FPT包括在小计中=是
1. 转到&#x200B;**商店** > **属性** > **产品**，然后创建类型为=固定产品税的新属性。
1. 将属性添加到属性集。
1. 从属性集创建两个产品，并为您的国家/地区和省/市/自治区配置FPT属性。
1. 将两个项目都添加到订单中。
1. 输入需要支付FPT的地址。
1. 下订单。
1. 检查订单上的物料列表。

<u>预期的结果</u>：

FPT显示在每个产品下。

<u>实际结果</u>：

这两个项目的FPT值都显示在第二个项目下。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
