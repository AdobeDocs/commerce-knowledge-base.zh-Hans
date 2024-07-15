---
title: 'MDVA-30963：管理员产品搜索筛选器未按预期工作'
description: MDVA-30963修补程序解决了Commerce管理员和产品搜索过滤器无法按预期工作的问题。 在筛选**所有存储视图**存储视图范围时，也会考虑在存储视图范围中覆盖的值。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8后，即可使用此修补程序。 请注意，Adobe Commerce 2.4.2中已修复此问题。
exl-id: bde2836e-8954-48e5-b411-08c951ec8620
feature: Admin Workspace, Products, Search
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# MDVA-30963：管理员产品搜索筛选器未按预期工作

MDVA-30963修补程序解决了Commerce管理员和产品搜索过滤器无法按预期工作的问题。 在筛选&#x200B;**所有存储视图**&#x200B;存储视图范围时，也会考虑在存储视图范围中覆盖的值。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8时，此修补程序可用。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.0

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.4.1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

1. 设置&#x200B;**商店** > **配置** > **目录** > **目录** > **价格** > **目录价格范围** = *网站*。
1. 创建两个使用两种不同货币的网站(例如，默认网站为印度商店\[卢比₹\]，第二个网站为美国商店\[美元$\])。
1. 设置以下&#x200B;**基本货币**、**默认显示货币**&#x200B;和&#x200B;**允许的货币**：
   * **默认配置** = *美元（默认）*
   * **主网站** = *印度卢比*
   * **WebsiteUS** = **使用默认值** = *美元*
1. 设置&#x200B;**商店** > **货币汇率** = *1:1*。
1. 创建一个分配给两个网站的简单测试产品，该产品价格如下：
   * **默认价格** = **美国网站价格** = *123 USD*
   * **主网站价格** = *321卢比*
1. 创建只能访问美国商店的subAdmin用户。
1. 转到美国店面，将产品放入购物车（例如： *123 USD price*）。
1. 使用刚刚创建的subAdmin登录到管理员（示例：*仅限美国admin*）。
1. 转到&#x200B;**报表** > **购物车中的产品**。

<u>预期的结果</u>：

在&#x200B;**所有存储视图**&#x200B;存储视图范围内进行筛选时，产品筛选应该获得该特定范围内的值集。

<u>实际结果</u>：

在筛选“所有存储视图”存储视图范围时，也会考虑存储视图范围中覆盖的值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
