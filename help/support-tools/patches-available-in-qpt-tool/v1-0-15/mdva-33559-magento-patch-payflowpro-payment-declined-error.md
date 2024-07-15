---
title: 'MDVA-33559修补程序：PayflowPro付款被拒绝错误'
description: MDVA-33559补丁解决了PayPal PayflowPro付款被拒绝的问题。
exl-id: aec57ffa-07c7-404e-985d-8ec4fdb019b1
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# MDVA-33559修补程序： PayflowPro付款已拒绝错误

MDVA-33559补丁解决了PayPal PayflowPro付款被拒绝的问题。

安装[Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15时，此修补程序可用。 请注意，该问题计划在Adobe Commerce版本2.4.3中修复。

## 受影响的产品和版本

**在Cloud Infrastructure 2.3.5-p2上为Adobe Commerce版本** Adobe Commerce创建修补程序

**与Adobe Commerce版本兼容：** Adobe Commerce on cloud infrastructure和Adobe Commerce内部部署2.3.0 - 2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

此问题与名称中使用的&amp;符号和等号(=)特殊字符有关。

<u>重现步骤</u>：

1. 将简单产品添加到购物车。
1. 去结帐。
1. 设置送货地址。 (示例送货地址： **名字** = ** *约翰的* ** **姓氏** = ** *苹果和橙子，公司* ** **街道地址** = *1234 E无名的St* **国家/地区** = *美国* **州/省** = *安州* **城市{2 1} = *Anytown*** Zip **= *12345***&#x200B;电话&#x200B;**= *1234567890*)**
1. 将付款设置为&#x200B;**PayPal PayflowPro**&#x200B;并尝试完成结帐。

<u>预期的结果</u>：

如预期，交易会导致付款成功或出现正确的错误消息。

<u>实际结果</u>：

交易被拒绝，客户收到一封电子邮件，上面写着“交易已被拒绝”。

## 应用修补程序

要应用单独的修补程序，请根据您的Adobe Commerce产品使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT工具中可用的其他修补程序的信息，请参阅QPT工具](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)中可用的[修补程序部分。
