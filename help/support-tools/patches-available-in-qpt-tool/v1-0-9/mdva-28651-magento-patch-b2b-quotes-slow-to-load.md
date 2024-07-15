---
title: 'MDVA-28651： B2B — 引号加载缓慢'
description: MDVA-28651修补程序解决了加载引号时出现多个性能问题的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9后，即可使用此修补程序。 请注意，此问题计划在Adobe Commerce版本2.4.2中修复。
exl-id: 2d0bfbba-cdf3-4f9e-a900-ce42909fac8e
feature: B2B, Quotes
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-28651：B2B — 引号加载缓慢

MDVA-28651修补程序解决了加载引号时出现多个性能问题的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.9时，此修补程序可用。 请注意，此问题计划在Adobe Commerce版本2.4.2中修复。

## 受影响的产品和版本

* 该补丁是为Cloud Infrastructure 2.3.4上的Adobe Commerce设计的。
* 该修补程序还与以下Adobe Commerce版本兼容：Adobe Commerce内部部署版和Adobe Commerce on cloud infrastructure 2.3.0-2.3.5-p1、2.4.0和2.4.1版。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户报价列表页面上的性能问题：

* 报价单列表的双加载：首先加载整个页面，其次是Ajax请求。
* 从插件中加载每个引号的循环。
* 当报价转换为快照时，将重复加载报价项。

<u>重现步骤</u>

1. 为客户分配了40多个引号。
1. 登录并浏览&#x200B;**我的引号**&#x200B;页面。

<u>实际结果</u>

完全加载&#x200B;**我的引号**&#x200B;页面内容（该页面的加载+网格中显示的数据）的响应时间约为45秒。

<u>预期的结果</u>

完全加载&#x200B;**我的引号**&#x200B;页面内容的响应时间应小于45秒。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
