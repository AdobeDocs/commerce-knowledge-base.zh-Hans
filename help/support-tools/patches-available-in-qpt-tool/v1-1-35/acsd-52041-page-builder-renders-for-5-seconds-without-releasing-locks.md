---
title: “ACSD-52041：页面生成器渲染不会释放锁定”
description: 应用ACSD-52041修补程序以修复Adobe Commerce问题，该问题导致页面生成器呈现五秒钟，并且不释放锁定。
feature: Page Builder
role: Admin, Developer
exl-id: f2a1fd36-2098-46a7-aa42-3a5a0014adc9
source-git-commit: b5c253a5c0651c6027c0795edb2f230bd65f734a
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-52041：页面生成器渲染不会释放锁定

ACSD-52041修补程序修复了页面生成器呈现5秒钟而不释放锁的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.48时，此修补程序可用。 修补程序ID为ACSD-52041-v2。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p5、2.4.5 - 2.4.5-p4和2.4.6 - 2.4.6-p2。



>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。


## 问题

**[!DNL Page Builder]**&#x200B;呈现&#x200B;*5*&#x200B;秒而不释放锁定。

<u>重现步骤</u>：

1. 编辑CMS页面、产品页面或具有&#x200B;**[!DNL Page Builder]**&#x200B;的任何内容。
1. 保存更改。
1. 请注意页面保存时间。

<u>预期的结果</u>

内容已保存。 浏览器日志中未找到错误。

<u>实际结果</u>

保存操作需要比平常更长的时间来完成。
控制台中的错误： ``Page Builder was rendering for 5 seconds without releasing locks``

## 应用修补程序

要为版本&#x200B;**2.4.4 - 2.4.4-p5、2.4.5 - 2.4.5-p4和2.4.6 - 2.4.6-p2**&#x200B;应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans>)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans>)。
