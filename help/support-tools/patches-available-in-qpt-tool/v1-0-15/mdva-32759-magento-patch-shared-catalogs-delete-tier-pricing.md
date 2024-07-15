---
title: 'MDVA-32759修补程序：共享目录删除层定价'
description: MDVA-32759修补程序解决了共享目录删除现有层定价的问题。
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# MDVA-32759修补程序：共享目录删除层定价

MDVA-32759修补程序解决了共享目录删除现有层定价的问题。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15时，此修补程序可用。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.4-p2

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>先决条件</u>：

安装启用了&#x200B;**B2B功能**&#x200B;的Adobe Commerce和B2B。

<u>重现步骤</u>：

1. 转到&#x200B;**商店>配置> B2B功能>启用公司**&#x200B;和&#x200B;**共享目录**。
1. 运行`bin/magento cron:run`。
1. 创建一个简单的产品，单击&#x200B;**高级定价**，添加&#x200B;**目录和层价格**，然后保存它。
1. 转到&#x200B;**目录>共享目录>设置定价和结构**，单击&#x200B;**配置**，然后从下拉菜单中，取消选择所有选项并保存。
1. 运行`bin/magento cron:run`。
1. 打开上面创建的产品，然后查看高级定价。

<u>预期的结果</u>：

按照预期，从公共共享目录中删除所有产品后，不应从产品中删除层级价格。

<u>实际结果</u>：

从公共共享目录中删除所有产品后，将删除该层价格。


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
