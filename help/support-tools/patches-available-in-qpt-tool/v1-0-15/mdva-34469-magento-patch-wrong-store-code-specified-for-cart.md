---
title: 'MDVA-34469：为购物车指定的存储代码错误'
description: “MDVA-34469修补程序解决了以下问题：切换商店视图后将产品添加到购物车时，用户收到错误消息：*为购物车指定的商店代码错误*。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15后，即可使用此修补程序。 修补程序ID为MDVA-34469。 请注意，Adobe Commerce 2.4.2中已修复此问题。'
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469：为购物车指定的存储代码错误

MDVA-34469修补程序解决了在切换商店视图后将产品添加到购物车时，用户收到错误消息&#x200B;*为购物车*&#x200B;指定的商店代码错误的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15时，此修补程序可用。 修补程序ID为MDVA-34469。 请注意，Adobe Commerce 2.4.2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.4.1 - 2.4.1-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户在尝试切换商店视图时看到购物车查询错误&#x200B;*“为购物车指定的商店代码错误”*。

<u>先决条件</u>：

* Adobe Commerce 2.4.0。
* 配置了具有单个商店和两个商店视图的单个网站。
* 创建客户帐户。

<u>重现步骤</u>：

1. Adobe Commerce后端配置为具有两个存储视图（使用存储代码：默认值、秒）。
1. 用户使用默认商店代码创建购物车。
1. 用户尝试使用`Store`请求标头中的第二个商店代码检索此购物车。

<u>预期的结果</u>：

之所以显示购物车，是因为切换商店（在`Store`请求标头中发送新代码）会将购物车与请求的商店关联。

<u>实际结果</u>：

购物车查询返回错误，并且购物车未显示。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
