---
title: 'MDVA-30815：Elasticsearch的空白搜索结果'
description: MDVA-30815修补程序修复了在更改搜索结果的限制符选项时Elasticsearch显示空白页的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。 请注意，Adobe Commerce 2.3.5中已修复此问题。
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815：Elasticsearch的空白搜索结果

MDVA-30815修补程序修复了在更改搜索结果的限制符选项时Elasticsearch显示空白页的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。 请注意，Adobe Commerce 2.3.5中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用Elasticsearch时，如果更改搜索结果的限制符选项，Adobe Commerce将显示一个空白页。

<u>先决条件</u>：

Elasticsearch **已启用**。 转到&#x200B;**存储** > **设置** > **配置** > **目录** > **目录搜索**。

<u>重现步骤</u>：

1. 转到您的网站。
1. 在主搜索字段中搜索产品。
1. 显示搜索结果页后，单击搜索结果页中的最后一页。
1. 从限制符选项中选择&#x200B;**每页显示xx**。 请确保这是不同于当前配置的搜索结果数限制。

<u>预期的结果</u>：

该页显示配置数量的产品结果。

<u>实际结果</u>：

显示空白页。 此错误也可在`var/report`中看到： *\&#39;&quot;0&quot;：&quot;SQLSTATE\[42000\]：语法错误或访问冲突： 1064您的SQL语法中有错误；请查阅与MySQL服务器版本对应的手册，以了解在&#39;\&#39;*&#x200B;附近使用的正确语法

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
