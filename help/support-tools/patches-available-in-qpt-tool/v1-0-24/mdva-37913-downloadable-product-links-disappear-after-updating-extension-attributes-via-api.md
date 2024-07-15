---
title: 'MDVA-37913：通过API更新扩展属性后，产品下载链接消失'
description: 的MDVA-37913修补程序解决了通过API更新扩展属性后可下载产品链接消失的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24后，即可使用此修补程序。 修补程序ID为MDVA-37913。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。
exl-id: e4b2cf59-5c35-4a28-a63e-15cd7d0d5a5d
feature: REST, Attributes, Extensions, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# MDVA-37913：通过API更新扩展属性后，产品下载链接消失

的MDVA-37913修补程序解决了通过API更新扩展属性后可下载产品链接消失的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24时，此修补程序可用。 修补程序ID为MDVA-37913。 请注意，该问题计划在Adobe Commerce 2.4.3中修复。


## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
云基础架构上的Adobe Commerce 2.3.6

**与Adobe Commerce版本兼容：**
Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.0 - 2.4.0-p1
>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。


## 问题

通过API更新扩展属性后，可下载的产品链接消失。

<u>先决条件</u>：
带有下载链接的可下载产品。

<u>重现步骤</u>：

1. 使用如下请求更新扩展属性：

```JSON
{
    "product": {
        "extension_attributes": {
            "stock_item": {
                "is_in_stock": true,
                "qty": 100
            }
        }
    }
}
```

<u>预期的结果</u>：<br>
产品已更新，所有下载链接都不会被删除。

<u>实际结果</u>：<br>
产品已更新，但已删除所有下载链接。


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce内部部署：[软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相关阅读

要在我们的支持知识库中了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

有关QPT工具中可用的其他修补程序的信息，请参阅我们的支持知识库中的[QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)部分。
