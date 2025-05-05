---
title: 'MDVA-39181：相关产品规则显示规则中未定义类别中的产品'
description: MDVA-39181修补程序解决了相关产品规则显示规则中未定义类别中的产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10后，即可使用此修补程序。 修补程序ID为MDVA-39181。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: b6364d1c-2480-483a-9a83-ac91feeb14b9
feature: Categories, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39181：相关产品规则显示规则中未定义类别中的产品

MDVA-39181修补程序解决了相关产品规则显示规则中未定义类别中的产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10时，此修补程序可用。 修补程序ID为MDVA-39181。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

相关产品规则显示规则中未定义类别的产品。

<u>先决条件</u>：

安装示例数据。

<u>重现步骤</u>：

1. 创建属性品牌并将其添加到&#x200B;**Tops属性集**。
1. 选择&#x200B;**Josie**、**Augusta**&#x200B;和&#x200B;**Ingrid**&#x200B;夹克以从&#x200B;**女性** > **上衣** > **夹克类别**&#x200B;添加到品牌猫咪中。
1. 选择&#x200B;**Beaumont**、**Hyperion**&#x200B;和&#x200B;**Kenobi**&#x200B;夹克以从&#x200B;**男士** > **上衣** > **夹克类别**&#x200B;添加到品牌猫咪中。
1. 使用以下方式创建相关产品：

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * 要匹配的产品：

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * 要显示的产品：

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. 从前端打开SKU WJ04并检查相关产品。
1. 从&#x200B;**女性** > **上衣** > **夹克**&#x200B;更新类别ID，以防它与此不同。

<u>预期的结果</u>：

只有相同品牌和相同子类别的产品才会显示在相关产品中。

<u>实际结果</u>：

相关产品显示的是同一品牌，但来自随机父类别。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
