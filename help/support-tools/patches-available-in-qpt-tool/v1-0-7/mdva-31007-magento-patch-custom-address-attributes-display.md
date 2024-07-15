---
title: 'MDVA-31007：自定义地址属性显示'
description: MDVA-31007修补程序解决了自定义地址属性在“我的帐户”区域和后端(在**Sales &amp；gt；订单**位置)的订单详细信息页面中无法正确显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 43c82b66-395f-4e33-8312-9a1994862f5f
feature: Attributes, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# MDVA-31007：自定义地址属性显示

MDVA-31007修补程序解决了自定义地址属性在“我的帐户”区域和后端（**Sales > Orders**&#x200B;位置）的订单详细信息页面中无法正确显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 登录到Admin后端。
1. 导航到&#x200B;**商店** > **属性** > **客户地址**。
1. 创建两个属性：

   * 设置输入类型： *下拉列表*。
   * 设置输入类型： *文本*。

1. 导航到&#x200B;**商店** > **配置** > **客户** > **客户配置**。
1. 选择&#x200B;*作用域*&#x200B;作为&#x200B;**默认存储**&#x200B;视图。
1. 展开&#x200B;**地址模板**&#x200B;部分。 更新&#x200B;*Text*、*Text One Line*&#x200B;和&#x200B;*HTML*&#x200B;以包含上述两个自定义属性：

   ```php
   {{depend testdropdown}}Dropdown: {{var testdropdown}}{{/depend}}    {{depend testtext}}Text: {{var testtext}}{{/depend}}
   ```

1. 打开店面。
1. 创建用户并使用其登录。
1. 转到&#x200B;**我的帐户** > **通讯簿**，然后添加新地址（填写两个自定义属性）。
1. 将产品添加到购物车，然后下订单。
1. 在订单成功页面上，单击&#x200B;**订单号**&#x200B;链接。
1. 在订单详细信息页面上，查看&#x200B;**订单信息**&#x200B;部分。
1. 转到&#x200B;**后端** > **销售** > **订单**，单击上面的订单，并观察&#x200B;**地址信息**&#x200B;部分。

<u>预期的结果</u>：

在前端和后端上，帐单地址和送货地址均按预期显示。

<u>实际结果</u>：

在前端和后端上，计费地址显示不正确。 下拉属性的选定选项缺失，且输入属性的值包含属性代码。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
