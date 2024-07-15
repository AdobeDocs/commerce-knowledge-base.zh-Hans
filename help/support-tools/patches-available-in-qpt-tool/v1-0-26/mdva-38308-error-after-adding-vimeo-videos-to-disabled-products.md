---
title: 'MDVA-38308：将Vimeo视频添加到已禁用的产品时出错'
description: “适用于Adobe Commerce的MDVA-38308质量修补程序解决了向禁用的产品添加Vimeo视频时，用户收到错误消息的问题：*注意：未定义的索引：/lib/internal/Magento/Framework/File/Uploader.php中的扩展806*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26后，即可使用此修补程序。 修补程序ID为MDVA-38308。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。'
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308：将Vimeo视频添加到禁用的产品时出错

适用于Adobe Commerce的MDVA-38308质量修补程序解决了向禁用的产品添加Vimeo视频时，用户收到以下错误消息的问题： *注意：未定义的索引： /lib/internal/Magento/Framework/File/Uploader.php第806行中的扩展*。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26时，此修补程序可用。 修补程序ID为MDVA-38308。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
云基础架构上的Adobe Commerce 2.4.1-p1、2.4.2-p1

**与Adobe Commerce版本兼容：**
Adobe Commerce内部部署和Adobe Commerce on cloud infrastructure 2.3.5 - 2.3.6-p1， 2.4.0 - 2.4.1-p1， 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将Vimeo视频添加到已禁用的产品时，您会收到以下错误消息： *注意：未定义的索引： /lib/internal/Magento/Framework/File/Uploader.php中的扩展806 online*

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 禁用创建的产品。
1. 尝试将Vimeo视频添加到已禁用的产品。

<u>预期的结果</u>：

添加视频时没有出现错误。

<u>实际结果</u>：

您会收到以下错误：
*注意：未定义的索引： /lib/internal/Magento/Framework/File/Uploader.php中的扩展806*&#x200B;行

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce内部部署：[软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* 云基础架构上的Adobe Commerce： [升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)

## 相关阅读

要在我们的支持知识库中了解有关Quality Patches Tool的更多信息，请参阅：

* [Quality Patches Tool released：一款用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [使用Quality Patches Tool检查是否有可用于Adobe Commerce问题的修补程序](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

有关QPT工具中可用的其他修补程序的信息，请参阅我们的支持知识库中的[QPT工具中可用的修补程序](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-)部分。
