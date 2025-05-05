---
title: 'MDVA-38666：管理员用户无法更改可配置的产品选项'
description: MDVA-38666修补程序解决了管理员用户无法更改客户购物车中可配置的产品选项的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-38666。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 72440e47-1deb-41da-a225-d4bc73029ad5
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# MDVA-38666：管理员用户无法更改可配置的产品选项

MDVA-38666修补程序解决了管理员用户无法更改客户购物车中可配置的产品选项的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9时，此修补程序可用。 修补程序ID为MDVA-38666。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

管理员用户无法更改客户购物车中的可配置产品选项。

<u>重现步骤</u>：

1. 将客户帐户范围设置为全局。
1. 使用商店创建两个网站。
1. 创建两个可配置的产品并将它们分配给每个网站。
1. 在前端创建客户帐户并登录。
1. 将产品添加到购物车并执行结账（此操作可使每个网站上的报价ID不同）。
1. 将产品添加到购物车中并保留它。
1. 切换到第二个网站并将产品添加到购物车（相同的登录应该有效，因为客户帐户范围设置为“全局”）。
1. 从管理员中打开客户并导航到购物车选项卡。
1. 从下拉列表中切换存储，然后尝试更改配置。

<u>预期的结果</u>：

用户会看到一个包含可配置选项的弹出窗口。

<u>实际结果</u>：

不显示弹出窗体。 用户无法更改配置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
