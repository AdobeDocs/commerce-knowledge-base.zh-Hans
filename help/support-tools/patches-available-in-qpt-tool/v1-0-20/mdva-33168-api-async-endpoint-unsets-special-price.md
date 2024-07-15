---
title: 'MDVA-33168： API异步端点取消设置特殊价格'
description: MDVA-33168修补程序修复了使用API异步端点更新产品属性时取消设置特殊价格的问题。
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168： API异步端点取消设置特殊价格

MDVA-33168修补程序修复了使用API异步端点更新产品属性时取消设置特殊价格的问题。

安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20时，此修补程序可用。 修补程序ID为MDVA-33168。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.3-p1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.3 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 使用商店创建两个网站。
1. 转到&#x200B;**商店>配置>目录>目录>价格>目录**&#x200B;并设置&#x200B;**价格范围** = *网站*。
1. 创建&#x200B;*text-type*&#x200B;产品属性。 将所有选项保留为默认值。
1. 将创建的属性添加到默认属性集。
1. 创建要与捆绑产品一起使用的简单产品。
1. 使用以下示例选项创建捆绑产品：
   * **启用产品** = *是*。
   * **属性集** = *默认值*。
   * **产品名称** = *捆绑包–1*。
   * **SKU** = *包–1*。
   * **动态SKU** = *是*。
   * **价格** = *$100.00*。
   * **税类** = *应纳税商品*。
   * **库存状态** = *库存*。
1. 在&#x200B;**捆绑项目**&#x200B;下，设置以下示例选项：
   * **装运捆绑包项目** = *在一起*。
   * **选项标题** = *测试*，**输入类型** = *单选按钮*，**必需**&#x200B;复选框= *已选中*。
   * **为默认值**&#x200B;复选框= *已取消选中*。
   * **名称** = *简单–100*。
   * **SKU** = *简单–100*。
   * **价格** = *100.00*。
   * **价格类型** = *固定*。
   * **默认数量** = *1*。
   * **用户定义的复选框**&#x200B;复选框= *取消选中*。
1. 将范围切换到非默认存储，并设置特殊价格。 （示例：在&#x200B;**高级定价**&#x200B;页面上，设置&#x200B;**特殊价格** = *4%*，且&#x200B;**价格视图** = *价格范围*。）
1. 仅在非默认存储范围中更新新属性，如以下示例：

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>预期的结果</u>：

使用异步Rest API更新产品属性时，其他属性值会按预期保持相同。

<u>实际结果</u>：

移除使用商店范围内的异步Rest API设置的特殊价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
