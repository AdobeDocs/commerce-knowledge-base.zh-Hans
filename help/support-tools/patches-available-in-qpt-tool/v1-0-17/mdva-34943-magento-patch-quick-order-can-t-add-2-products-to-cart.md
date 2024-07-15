---
title: “MDVA-34943：快速订单无法将2个以上的产品添加到购物车”
description: MDVA-34943修补程序解决了快速订单无法将两个或多个产品添加到购物车的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.2中已修复此问题。
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943：快速订单无法将2个以上的产品添加到购物车

MDVA-34943修补程序解决了快速订单无法将两个或多个产品添加到购物车的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17时，此修补程序可用。 请注意，Adobe Commerce版本2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.0-p1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法将两个或更多产品快速添加到购物车。

<u>先决条件</u>：

Adobe Commerce和简单产品。

<u>重现步骤</u>：

1. 转到店面上的&#x200B;**快速订购**（未登录时）。
1. 输入有效的SKU，单击自动完成字段中显示的产品，然后设置&#x200B;**数量** = *1*。
1. 输入相同的有效SKU，但更改第一个字符的大小写（将大写更改为小写，或将小写更改为大写），然后单击自动完成字段中显示的产品，并设置&#x200B;**数量** = *1*。
1. 输入&#x200B;**SKU**&#x200B;的`random_sting_value`，并设置&#x200B;**数量** = *1*。
1. 设置&#x200B;**SKU** = *123123123*，设置&#x200B;**数量** = *1*。
1. 删除所有内容，但添加到&#x200B;**快速订购**&#x200B;页面中的第一个条目除外。
1. 在&#x200B;**输入多个SKU**&#x200B;字段中输入第一个SKU（与上述步骤2类似），然后单击&#x200B;**添加到列表**。
1. 这会导致第一个SKU的数量为2，`random_sting_value`的行数量为2。
1. 要执行更多测试，请刷新页面。
1. 这不会像预期的那样生成快速订购的SKU。
1. 在&#x200B;**输入多个SKU**&#x200B;字段中输入`random_sting_value2`，然后单击&#x200B;**添加到列表**。
1. 这会生成两个以前存在的有效SKU和`random_sting_value2`。

<u>预期的结果</u>：

两个或更多产品能够按预期添加到购物车。

<u>实际结果</u>：

当转到&#x200B;**购物车**&#x200B;页面时，第一个添加的产品正常显示，但对于第二个产品以及任何添加到购物车的后续产品，将显示“*1产品需要注意*”错误消息。 第二个或任何其他产品将列在&#x200B;**购物车**&#x200B;页面的&#x200B;**产品需要注意**&#x200B;部分。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
