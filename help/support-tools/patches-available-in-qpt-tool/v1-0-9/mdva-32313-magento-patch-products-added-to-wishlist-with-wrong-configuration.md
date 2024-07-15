---
title: 'MDVA-32313修补程序：产品已添加到包含错误配置的愿望清单'
description: MDVA-32313修补程序解决了无法将可配置产品正确添加到愿望列表的问题，因为在将可配置产品添加到愿望列表时，会向这些产品分配错误的配置。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10后，即可使用此修补程序。 请注意，Adobe Commerce版本2.4.2中已修复此问题。
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-32313修补程序：使用错误的配置添加到愿望清单中的产品

MDVA-32313修补程序解决了无法将可配置产品正确添加到愿望列表的问题，因为在将可配置产品添加到愿望列表时，会向这些产品分配错误的配置。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10时，此修补程序可用。 请注意，Adobe Commerce版本2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.0

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 创建客户。
1. 登录到客户帐户。
1. 导航到&#x200B;**产品列表**&#x200B;页面。
1. 选择一个可配置的产品（例如： *configurable\_1* ），然后在&#x200B;**产品列表**&#x200B;页面中选择首选的颜色和大小选项（**不要打开产品页面。**）。
1. 单击同一页面上其他可配置产品（例如： *configurable\_2*）的愿望清单图标，而不选择任何颜色/大小选项。

<u>预期的结果</u>：

*configurable\_2*&#x200B;产品已按预期添加到愿望清单，但未选择任何选项。

<u>实际结果</u>：

使用&#x200B;*configurable\_1*&#x200B;产品的配置将&#x200B;*configurable\_2*&#x200B;产品添加到愿望清单。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
