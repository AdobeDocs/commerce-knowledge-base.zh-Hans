---
title: 'MDVA-40134：启用共享目录后，GraphQL未返回相关产品'
description: MDVA-40134修补程序修复了在启用共享目录后，GraphQL未返回相关产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-40134。 请注意，Adobe Commerce 2.4.3中已修复此问题。
exl-id: 7b14355a-1c14-4c80-9426-6c40505d638b
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-40134：启用共享目录后，GraphQL未返回相关产品

MDVA-40134修补程序修复了在启用共享目录后，GraphQL未返回相关产品的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-40134。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

启用共享目录后，GraphQL不会返回相关产品。

<u>先决条件</u>：

必须安装B2B模块。
必须只使用示例数据清空实例。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **配置** > **常规** > **B2B功能**&#x200B;并启用&#x200B;**公司和共享目录**。
1. 转到&#x200B;**目录** > **共享目录**&#x200B;并将所有产品添加到&#x200B;**常规目录**。
1. 使用样本数据修改Joust Duffle Bag (SKU 24-MB01)。
1. 在&#x200B;**相关产品**&#x200B;下，添加两个饺子包（ID 7和13）。
1. 发送&#x200B;**Post**&#x200B;请求：

<pre>{
  products(filter： {sku： {eq： "24-MB01"}}，sort： {name： ASC}) {
    项目{
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u>预期的结果</u>：

GraphQL响应中将显示相关产品。

<u>实际结果</u>：

用户收到以下错误：

<pre>Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor：：getStoreId()的返回值必须是int类型，null返回{"exception"："[object] (GraphQL\\Error\\Error(code： 0)： Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor：：getStoreId()的返回值必须是int类型，返回的是null </pre>

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
