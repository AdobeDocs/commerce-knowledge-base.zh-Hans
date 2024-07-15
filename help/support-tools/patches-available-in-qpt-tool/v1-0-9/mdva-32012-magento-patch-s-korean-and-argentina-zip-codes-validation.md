---
title: 'MDVA-32012修补程序：韩国和阿根廷邮政编码验证'
description: MDVA-32012补丁解决了阿根廷和韩国邮政编码因国家邮政编码格式更改或变化而无法验证的问题。 韩国邮政编码现在要求为5位数，而以前为6位数。 阿根廷邮政编码可以同时为数字和字母数字。 MDVA-32012补丁意味着这些邮政编码值格式将适用于这些国家/地区。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9后，即可使用此修补程序。 请注意，该问题计划在Adobe Commerce版本2.4.2中修复。
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# MDVA-32012修补程序：韩国和阿根廷邮政编码验证

MDVA-32012补丁解决了阿根廷和韩国邮政编码因国家邮政编码格式更改或变化而无法验证的问题。 韩国邮政编码现在要求为5位数，而以前为6位数。 阿根廷邮政编码可以同时为数字和字母数字。 MDVA-32012补丁意味着这些邮政编码值格式将适用于这些国家/地区。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9时，此修补程序可用。 请注意，该问题计划在Adobe Commerce版本2.4.2中修复。

## 受影响的产品和版本

* 该补丁是为Cloud Infrastructure 2.3.5上的Adobe Commerce设计的。
* 该修补程序还与以下Adobe Commerce版本兼容：云基础架构上的Adobe Commerce以及Adobe Commerce内部部署2.3.0 - 2.4.1。

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

输入5位数的韩国或阿根廷字母数字邮政编码会产生警告：

*提供的邮政编码似乎无效。 示例： [1234（如果输入的是字母数字的阿根廷地址）]或[123-456（如果输入的是5位数的韩国地址）]。 如果您认为它是正确的，则可以忽略此通知。*

<u>重现步骤</u>：

1. 打开店面。
1. 将项目添加到购物车。
1. 结账流程。
1. 为国家/地区添加一个新地址（含韩国）并输入5位数的邮政编码，或为国家/地区添加一个新地址（含阿根廷）并输入字母数字邮政编码。
1. 尝试保存。

<u>预期的结果</u>：

地址应在不发出警告的情况下保存。

<u>实际结果</u>：

保存地址将返回警告。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)中提供的[修补程序。
