---
title: '''ACSD-46938：在''setup：upgrade''期间数据库触发器出现性能问题'
description: 应用ACSD-46938修补程序以修复Adobe Commerce问题，该问题导致“setup：upgrade”命令将索引器模式从计划更改为保存，从而显着降低性能。
feature: Upgrade
role: Admin, Developer
source-git-commit: cbd16ac7c6d6d7a4e3786880409475a10964c070
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46938：在`setup:upgrade`期间数据库触发器出现性能问题

ACSD-46938修补程序修复了`setup:upgrade`命令将索引器模式从计划更改为保存，从而导致性能显着下降的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-46938。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在`setup:upgrade`中重新创建DB触发器期间性能下降。

<u>重现步骤</u>：

1. 创建一个包含许多产品和类别的大型目录。
1. 登录到[!UICONTROL Admin]。
1. 将所有索引器设置为[!UICONTROL Update By Schedule]模式。
1. 打开任何产品。
1. 更新它。 例如，为其分配一个新类别。
1. 单击[!UICONTROL Save]。
1. 并行运行`bin/magento setup:upgrade`和`bin/magento cron:run`命令。

<u>预期的结果</u>：

同时执行`bin/magento cron:run`命令时，`bin/magento setup:upgrade`命令的执行时间会显着增加。

<u>实际结果</u>：

命令的执行时间不会增加。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。