---
title: 'MDVA-31282：Paypal PayFlow Pro的双重授权'
description: MDVA-31282修补程序解决了在Adobe Commerce中的Paypal PayFlow Pro上发生双重授权的问题。 这种双重授权还产生了绕过PayFlow Pro欺诈筛选器和将交易费用翻倍的效果。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。
exl-id: f239012e-e1bd-474b-aad2-7218ec3a3d1b
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# MDVA-31282：Paypal PayFlow Pro的双重授权

MDVA-31282修补程序解决了在Adobe Commerce中的Paypal PayFlow Pro上发生双重授权的问题。 这种双重授权还产生了绕过PayFlow Pro欺诈筛选器和将交易费用翻倍的效果。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.3和2.3.5 - 2.3.6

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在Adobe Commerce的PayPal PayFlow Pro中会出现双重授权，这会绕过PayFlow Pro的欺诈筛选器和将交易费用加倍。

<u>先决条件</u>：

配置PayPal PayFlow Pro支付方式。

<u>重现步骤</u>：

1. 作为客人前往前端。
1. 将产品从产品页面添加到&#x200B;**购物车**。
1. 继续执行&#x200B;**签出**。
1. 将&#x200B;**送货地址**&#x200B;指定为国家/地区\#1中的地址（例如：英国地址），并选择送货方式。
1. 选择&#x200B;**PayPal PayFlow Pro**&#x200B;作为付款方式。 将&#x200B;**帐单地址**&#x200B;指定为国家/地区\#2中的地址（例如：美国地址）。
1. 输入信用卡数据并下订单。
1. 导航到管理员中的&#x200B;**Sales** > **Orders**，并观察创建的订单。

<u>预期的结果</u>：

* 付款信息块显示： *&quot;触发的欺诈过滤器： RESPMSG：欺诈服务正在审查*。 *订单处于可疑欺诈状态“*”。
* Paypal PayFlow Pro按预期显示单个授权交易。

<u>实际结果</u>：

* 付款信息块显示： *&quot;触发的欺诈过滤器： RESPMSG：欺诈服务正在审查*。 *订单处于处理状态“*”。
* Paypal PayFlow Pro显示双重授权交易。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
