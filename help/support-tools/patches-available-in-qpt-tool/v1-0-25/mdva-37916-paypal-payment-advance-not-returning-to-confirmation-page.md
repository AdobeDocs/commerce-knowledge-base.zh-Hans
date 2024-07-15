---
title: 'MDVA-37916：PayPal Payments Advanced未返回确认页面'
description: 适用于Adobe Commerce的MDVA-37916质量修补程序修复了PayPal Payments Advanced在付款后未返回到确认页面的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25后，即可使用此修补程序。 修补程序ID为MDVA-37916。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
exl-id: 18d7bb1c-d73a-43f6-90a8-650290dfd114
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# MDVA-37916：PayPal Payments Advanced未返回到确认页面

适用于Adobe Commerce的MDVA-37916质量修补程序修复了PayPal Payments Advanced在付款后未返回到确认页面的问题。 安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25时，此修补程序可用。 修补程序ID为MDVA-37916。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
云基础架构上的Adobe Commerce 2.3.6-p1

**与Adobe Commerce版本兼容：**
Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.6-2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用PayPal付款高级方法付款后，客户不会被带到“付款确认”页面。

<u>重现步骤</u>：[Screencast](https://assets.adobe.com/public/025d479b-5796-4772-6f3d-adc86306a799)

1. 将产品添加到购物车并导航到结账页面的支付步骤。
1. 选择&#x200B;**信用卡(Payflow Advanced)**&#x200B;付款选项。
1. 单击&#x200B;**继续**&#x200B;以使用付款表单打开iframe。
1. 使用沙盒信用卡详细信息填写付款表单。
   * 卡号：4444 3333 2222 1111或4111 111 1111 1111
   * 过期日期：2023年12月23日
   * CSC：123
1. 单击&#x200B;**立即付款**。

<u>预期的结果</u>：

在处理付款且付款成功后，您将被重定向至“订单确认”页。

<u>实际结果</u>：

* 系统不会将您重定向到“订单确认”页面。
* 但订单是在Adobe Commerce中创建的。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce内部部署：[软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相关阅读

要在我们的支持知识库中了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

有关QPT工具中可用的其他修补程序的信息，请参阅我们的支持知识库中的[QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)部分。
