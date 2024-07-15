---
title: 'MDVA-28993：Elasticsearch部分搜索，“最小值应匹配”并修复“带连字符的搜索”问题'
description: MDVA-28993修补程序实现了“最小应当匹配”功能和部分搜索Elasticsearch引擎，并解决了搜索查询中的连字符问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6后，即可使用该修补程序。
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993：Elasticsearch部分搜索，“最小值应匹配”并修复了“搜索时带有连字符”的问题

MDVA-28993修补程序实现了“最小应当匹配”功能和部分搜索Elasticsearch引擎，并解决了搜索查询中的连字符问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6时，该修补程序可用。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.4上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce内部部署/ Adobe Commerce on cloud infrastructure 2.3.4-2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。


## 问题

使用Elasticsearch6搜索包含连字符(-)的SKU时，搜索返回的结果过多。

<u>要再现的步骤：</u>

1. 去店面。

1. 在搜索栏中输入包含连字符的字符串，例如“WS-M-Blue”。

<u>预期结果：</u>

仅返回WS-M-Blue。

<u>实际结果：</u>

返回以“WS”开头的所有SKU。

## 补丁程序详细信息

MDVA-28993修补程序包含以下修复和改进：

* 实施新的“最小值应匹配”功能和部分Elasticsearch搜索引擎。 有关配置详细信息，请参阅用户指南中的[配置目录搜索](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match)。
* 部分搜索Elasticsearch
* 修复了上述的“使用连字符搜索”问题。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
