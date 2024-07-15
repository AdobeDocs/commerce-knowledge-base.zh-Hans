---
title: 'MDVA-29787：不显示相关产品'
description: MDVA-29787修补程序解决了Adobe Commerce商店前端未显示**相关产品**的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 修补程序ID为MDVA-29787。
exl-id: ee060d7b-3b0e-4bd5-84e6-fbd6d2fa532f
feature: Cache, Marketing Tools, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# MDVA-29787：不显示相关产品

MDVA-29787修补程序解决了Adobe Commerce商店前端未显示&#x200B;**相关产品**&#x200B;的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6时，此修补程序可用。 修补程序ID为MDVA-29787。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.3。

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.3.0 - 2.4.0。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当“*”是*&#x200B;条件之一，且在Commerce管理员中将&#x200B;**要显示的产品**&#x200B;用于时，**相关产品**&#x200B;的目标规则不起作用。

>[!NOTE]
>
>注意：此修补程序无法修复现有的目标规则。 必须重新创建现有的目标规则。

<u>重现步骤</u>：

1. 创建&#x200B;**新属性**（示例： Test\_Attr）。
   * 为存储所有者设置&#x200B;**目录输入类型** = *文本。*
   * 在&#x200B;**店面属性**&#x200B;中，设置&#x200B;**用于促销规则条件** = *是*。
1. 创建&#x200B;**新属性集**（示例： Test\_Set）。
1. 将&#x200B;**新属性**&#x200B;添加到&#x200B;**新属性集**（示例：将“Test\_Attr”属性添加到“Test\_Set”属性集）。
1. 创建三个产品。 对于示例，它们的设置如下所示：
   * 产品1，Test\_Attr = MAGT2NA\_Test3
   * 产品2，Test\_Attr = 24-MB02
   * 产品3，Test\_Attr = 701644329389M
1. 创建目标&#x200B;**规则** (**营销**   > **相关产品规则**，然后单击&#x200B;**添加规则**&#x200B;按钮。) 设置：
   * **应用于** = *相关产品*
   * **要匹配的产品**
   * 将您在&#x200B;****&#x200B;步骤1中创建&#x200B;**的新属性设置为Product1的属性（示例： Test\_Attr = MAGT2NA\_Test3）。**
   * **要显示的产品** =其他两个产品的属性(例如：24-MB02和701644329389M属性)。
1. 保存&#x200B;**规则**。
1. 如果需要，运行重新索引。
1. 清除缓存。
1. 在前端打开Product1。

<u>预期的结果</u>：

存在相关产品。

<u>实际结果</u>：

缺少相关产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
