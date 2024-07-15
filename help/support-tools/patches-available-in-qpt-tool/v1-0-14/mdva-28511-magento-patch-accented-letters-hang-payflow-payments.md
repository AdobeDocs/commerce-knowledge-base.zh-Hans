---
title: 'MDVA-28511：带重音字母挂起的付款流付款'
description: MDVA-28511修补程序解决了通过**Payflow Pro**对带有重音字母的客户名称付款不完整的问题。
exl-id: ecc827e3-2a1c-4f32-a0e2-9c5792483e7d
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# MDVA-28511：带重音符号的字母挂起Payflow付款

MDVA-28511修补程序解决了通过&#x200B;**Payflow Pro**&#x200B;进行的客户名称带有重音字母的付款未完成的问题。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14时，此修补程序可用。 请注意，Adobe Commerce版本2.3.6中已修复此问题。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.5-p1上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.5 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

<u>预修课程</u>：

启用&#x200B;**Payflow Pro**&#x200B;信用卡付款方式。

<u>重现步骤</u>：

1. 将产品添加到购物车并继续进入结帐页面。
1. 设置带有重音字母的客户名称。 （示例：**Aatienne Aaillin**）
1. 继续支付步骤。
1. 选择&#x200B;**Payflow Pro**&#x200B;作为&#x200B;**信用卡**&#x200B;并填写信用卡详细信息。
1. 单击&#x200B;**下单**&#x200B;按钮。

<u>预期的结果</u>：

订单如预期般顺利完成。

<u>实际结果</u>：

订单未完成，日志将显示与此示例类似的错误：

```php
[2020-06-12 07:50:23] report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted: �?tienne �?illini [] []
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的[修补程序部分。
