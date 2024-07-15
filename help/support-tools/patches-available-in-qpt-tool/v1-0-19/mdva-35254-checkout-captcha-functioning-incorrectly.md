---
title: 'MDVA-35254：签出CAPTCHA运行不正确'
description: MDVA-35254修补程序修复了在尝试签出第三方付款失败后CAPTCHA字段不显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-35254。 请注意，Adobe Commerce版本2.4.3中已修复此问题。
exl-id: 226c672b-3740-4a87-9ea1-66892acb9fe2
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MDVA-35254：签出CAPTCHA功能不正确

MDVA-35254修补程序修复了在尝试签出第三方付款失败后CAPTCHA字段不显示的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19后，即可使用此修补程序。 修补程序ID为MDVA-35254。 请注意，Adobe Commerce版本2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.1 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>重现步骤</u>：

配置验证码：

1. 安装和配置第三方支付提供商(例如：Braintree)。
1. 转到&#x200B;**Store > Configuration > Customer > Customer Configuration > CAPTCHA > Forms**。
1. 选择&#x200B;**结帐/下单**。
1. 将&#x200B;**次不成功的登录尝试次数保留为默认值** （默认值= *3*）。
1. 以客户身份登录。
1. 将任何产品添加到购物车。
1. 转到结帐中的付款部分。
1. 选择&#x200B;**信用卡**&#x200B;付款方式(示例：Braintree)。
1. 尝试三次失败的付款。

<u>预期的结果</u>：

当达到失败尝试的次数时，将显示CAPTCHA字段。

<u>实际结果</u>：

CAPTCHA字段从不显示，只显示错误消息： *请提供CAPTCHA代码并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
