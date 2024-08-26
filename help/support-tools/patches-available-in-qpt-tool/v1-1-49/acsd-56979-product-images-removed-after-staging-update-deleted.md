---
title: 'ACSD-56979：删除暂存更新后已删除产品映像'
description: 应用ACSD-56979修补程序以修复在删除暂存更新后删除产品映像的Adobe Commerce问题
feature: Products
role: Admin, Developer
source-git-commit: e97850bcaa98b1ccc1522fb6ee0046cd38bf1c93
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-56979：删除暂存更新后删除的产品映像

ACSD-56979修补程序修复了在删除暂存更新之后删除产品映像的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49时，此修补程序可用。 修补程序ID为ACSD-56979。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce和Magento Open Source版本兼容：**

* Adobe Commerce（所有部署方法）>=2.4.3 &lt;2.4.7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

删除暂存更新后会删除产品图像。

<u>重现步骤</u>：

1. 在Commerce管理员侧边栏中，转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;并创建产品。
1. 在&#x200B;**[!UICONTROL Images and Videos]**&#x200B;下，上传图像并保存产品。
1. 在&#x200B;**[!UICONTROL Scheduled Changes]**&#x200B;框中，选择&#x200B;**[!UICONTROL Schedule New Update]**。
   1. 选择几分钟之后的开始日期。
   1. 请勿选择结束日期。
1. 在&#x200B;**[!UICONTROL Scheduled Changes]**&#x200B;框中，选择&#x200B;**[!UICONTROL View/Edit]**&#x200B;链接。
1. 转到&#x200B;**[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]**&#x200B;并选择&#x200B;**[!UICONTROL Done]**。
1. 刷新页面。

<u>预期的结果</u>：

由于更新在计划的开始日期之前删除，因此产品应保持不变。

<u>实际结果</u>：

图像内容将丢失并显示零字节。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。