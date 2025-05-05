---
title: “MDVA-42645：管理员无法退款禁用商店积分的奖励积分”
description: MDVA-42645修补程序解决了在禁用商店点数功能时，管理员无法退款奖励点数的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42645。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645：管理员无法退还禁用商店点数的奖励积分

MDVA-42645修补程序解决了在禁用商店点数功能时，管理员无法退款奖励点数的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42645。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果禁用商店点数功能，则管理员无法退款奖励积分。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 创建新的客户帐户并添加一些奖励积分。
1. 通过转至&#x200B;**商店** >设置> **配置** > **客户** > **客户配置** > **商店点数选项**&#x200B;来禁用商店点数功能。
1. 以已分配奖励积分的客户身份登录。
1. 将产品添加到购物车并导航到结帐。
1. 使用支付部分的奖励点数下达订单。
1. 在管理员中打开订单并开具发票。
1. 单击&#x200B;**贷项通知单**&#x200B;链接以创建新的贷项通知单。
1. 勾选底部的“退款奖励积分”选项，然后单击“离线退款”**&#x200B;**。

<u>预期的结果</u>：

* 已成功创建贷项通知单。
* 奖励积分已成功退款。

<u>实际结果</u>：

您收到以下错误消息： *您不能使用超过订单金额的商店积分。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序。
