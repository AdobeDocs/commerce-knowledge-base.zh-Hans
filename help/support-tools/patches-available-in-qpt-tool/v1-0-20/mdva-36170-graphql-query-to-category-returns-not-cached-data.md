---
title: 'MDVA-36170：对类别的GraphQL查询返回非缓存数据'
description: MDVA-36170修补程序修复了未缓存GraphQL查询结果的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20后，即可使用此修补程序。 修补程序ID为MDVA-36170。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: 6249b751-4b71-4833-ab86-ded615d648a8
feature: Cache, GraphQL, Categories
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-36170：对类别的GraphQL查询返回非缓存数据

MDVA-36170修补程序修复了未缓存GraphQL查询结果的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20时，此修补程序可用。 修补程序ID为MDVA-36170。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.1 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

修复了未缓存GraphQL查询结果的问题。

<u>重现步骤</u>：

商家正在使用GET方法进行GraphQL缓存，但未获取缓存的数据。

<pre>https://magento_url/graphql?query={ products(filter： {category_id： {eq： "2"}}， pageSize： 2000， currentPage： 1， sort： {position： ASC}) {
项目{
  sku
  id
  name
  描述{
    html
  }
  url_key
  规范
  图像{
    标签
    gallery_url
  }
  __typename
  quantity_in
  small_image {
    gallery_url
    标签
  }
  product_price_range {
    maximum_price {
      final_price {
        值
      }
    }
    minimum_price {
      final_price {
        值
      }
    }
  }
  ...位于ConfigurableProduct {
    变体{
      属性{
        代码
        标签
        value_index
      }
      产品{
        sku
        quantity_in
      }
    }
   }
  }
}
}}</pre>

<u>预期的结果</u>：

数据已缓存。

<u>实际结果</u>：

不缓存数据。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
