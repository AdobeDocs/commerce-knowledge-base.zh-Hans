---
title: 'MDVA-33281修补程序：清单不一致问题'
description: MDVA-33281修补程序修复了三个清单不一致问题。 单击问题部分下面的链接问题，查看重现这些错误的步骤。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14后，即可使用此修补程序。
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-33281修补程序：清单不一致问题

MDVA-33281修补程序修复了三个清单不一致问题。 单击问题部分下面的链接问题，查看重现这些错误的步骤。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14时，此修补程序可用。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.5-p1

**与Adobe Commerce版本兼容：**

云基础架构上的Adobe Commerce 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

该修补程序修复了清单不一致问题，例如：

* 在CLI中运行`bin/magento inventory:reservation:list-inconsistencies`时，由于SKU参数类型错误，**PHP致命错误**。
* 在不一致列表中&#x200B;**重复数据**。
* **新预订**&#x200B;将在下订单前创建（以前实现基于下订单后的预订）。 如果订购过程中出现错误，将添加额外的预订以进行补偿。

>[!NOTE]
>
>还有一个修补程序MDVA-30112，它解决了`inventory_reservation`表中开发人员文档中[保留不一致](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies)数量异常大的问题。 有关解决方案，请参阅我们的支持知识库中的[MDVA-30112Magento修补程序：大量保留不一致](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md)。

## PHP致命错误

<u>重现步骤</u>：

运行`bin/magento inventory:reservation:list-inconsistencies`时出现PHP致命错误。

要获取保留不一致列表，请登录到生产服务器，然后在CLI中运行以下命令（ — r开关 — 原始输出）：

<pre>bin/magento inventory:reservation:列表不一致 — r</pre>

<u>预期的结果</u>：

将创建保留不一致列表。 这些将以下列格式返回

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>实际结果</u>：

PHP致命错误已输出。

## 重复数据

`inventory_reservation table`中存在重复数据。

<u>重现步骤</u>：

要对保留不一致问题进行故障诊断，请运行以下命令：

<pre>选择*， COUNT(*)
FROM inventory_reservation
按元数据、SKU、数量分组
COUNT(*) &gt; 1</pre>

<u>预期的结果</u>：

无重复项。

<u>实际结果</u>：

存在重复项。

## 新建预订

<u>重现步骤</u>：

在下单前创建的新预订：

1. 导入数据库。
1. 在终端中运行`bin/magento setup:upgrade`。
1. 在终端中运行`bin/magento inventory:reservation:list-inconsistencies        -i -r`以列出不一致。

<u>预期的结果</u>：

没有循环，结果更快。

<u>实际结果</u>：

相同的结果会以无限循环显示，或者命令因`memory_limit`而失败，具体取决于系统设置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
