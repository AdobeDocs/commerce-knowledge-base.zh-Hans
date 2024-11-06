---
title: 'MDVA-39163：新注册的来宾会话中的产品用户无法使用配送方式'
description: MDVA-39163修补程序解决了在注册新用户且购物车中的产品来自来宾会话时配送方式不可用的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-39163。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: f8661a4e-5832-41bb-be3d-4ea6c863fdb9
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# MDVA-39163：新注册的来宾会话产品用户无法使用配送方式

MDVA-39163修补程序解决了在注册新用户且购物车中的产品来自来宾会话时配送方式不可用的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9时，此修补程序可用。 修补程序ID为MDVA-39163。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

注册新用户后，配送方式不可用，购物车中的产品来自访客会话。

<u>重现步骤</u>：

1. 转到&#x200B;**管理员** > **商店** > **配置** > **销售** > **交付方法**。 仅启用&#x200B;**统一费率**&#x200B;配送方式并禁用其他所有方式。
1. 在&#x200B;**统一费率**&#x200B;配送方式中，选择&#x200B;**收货国家/地区**&#x200B;设置中可用的&#x200B;**特定**&#x200B;国家/地区选项，然后从列表中选择一个国家/地区（例如，美国）。
1. 转到&#x200B;**管理员** > **商店** > **配置** > **客户** > **客户配置**，并将&#x200B;**需要电子邮件确认**&#x200B;设置为&#x200B;_是_。
1. 在&#x200B;**管理员** > **营销** > **电子邮件模板**&#x200B;中创建新电子邮件模板，并加载`Footer (magento/luma)`模板并将模板内容替换为CMS块。

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. 转到&#x200B;**管理员** > **内容** > **设计** > **配置**，然后选择与前端网站相关的主题。 将“页脚模板”设置为创建的新电子邮件模板。
1. 转到前端并将产品添加到购物车。
1. 创建客户；您将收到一封确认电子邮件地址的电子邮件。 单击验证链接。 您将登录到网站。
1. 转到&#x200B;**我的帐户**&#x200B;并添加地址。 将地址国家/地区设置为您之前在管理员配置中设置的装运国家/地区。
1. 去结帐。

<u>预期的结果</u>：

发运方法可用，因为客户有一个与发运国家/地区兼容的地址。

<u>实际结果</u>：

配送方式不可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
