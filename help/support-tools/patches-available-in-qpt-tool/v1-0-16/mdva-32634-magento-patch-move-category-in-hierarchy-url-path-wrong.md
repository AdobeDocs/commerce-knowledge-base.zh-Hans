---
title: 'MDVA-32634修补程序：层次结构url_path中的移动类别错误'
description: MDVA-32634修补程序解决了在层次结构中移动类别后，目录类别的url\_path未更改的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: a445dea6-3834-479b-9044-b6d2b863a0b5
feature: Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# MDVA-32634修补程序：层次结构url_path中的移动类别错误

MDVA-32634修补程序解决了在层次结构中移动类别后，目录类别的url\_path未更改的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.1 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在层次结构中移动目录类别会导致url\_path不正确。 在层次结构中移动类别后，分配给默认存储作用域\[ **id：0** \]的类别的url\_path保持不变。

<u>重现步骤</u>：

1. 登录到Commerce管理员。 在根类别下创建以下类别结构： move-cat sub-move-cat sub-move-cat2 new-cat-move
1. 使用以下查询验证\[ catalog\_category\_entity\_varchar \]表中值分配的类别\[ url\_path \]属性\[ id： 120 \]：

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   它应会为您提供以下结果：

   ```sql
   MariaDB [m24dev]> SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 4;
   ```

   已生成\[ url\_path \]值并将其分配给所有存储范围\[ 0 \]。 与不具有B2B的实例相比，这是正确的。
1. 转到后端类别列表，将\[ move-cat \]拖放到\[ new-cat-move \]中。 现在，类别应该如下所示：new-cat-move-cat sub-move-cat sub-move-cat2
1. 使用以下查询检查\[ catalog\_category\_entity\_varchar \]表：

   ```sql
   SELECT * FROM catalog_category_entity_varchar WHERE attribute_id = 120 ORDER BY value_id DESC LIMIT 16;
   ```

<u>预期的结果</u>：

分配给所有存储作用域\[ 0 \]的url\_path也应该使用新路径进行更新。

<u>实际结果</u>：

分配给所有存储作用域\[ 0 \]的url\_path保持不变，即使移动后没有此类路径可用。 此外，它还为每个存储创建了新的url\_path值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
