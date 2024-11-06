---
title: 'ACSD-47027：慢查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新'
description: 应用ACSD-47027修补程序以修复查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL] 更新缓慢的Adobe Commerce问题。
exl-id: 478ae16b-7722-4469-8f8a-a38820e61ae4
feature: B2B, Companies, GraphQL, Roles/Permissions
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-47027：查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL]更新缓慢

ACSD-47027修补程序解决了慢速查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL]更新无法按预期工作的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23时，此修补程序可用。 修补程序ID为ACSD-47027。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

慢速查询B2B [!UICONTROL CompanyRole] [!DNL GraphQL]更新无法按预期工作。

<u>先决条件</u>：

安装B2B模块。

<u>重现步骤</u>：

1. 在Adobe Commerce管理员中，转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configurations]** > **[!UICONTROL B2B Features]**，并将&#x200B;**[!UICONTROL Enable Company]**&#x200B;设置为&#x200B;_是_。
1. 前往前端，创建公司。
1. 以公司用户身份登录后，转到&#x200B;**[!UICONTROL My Account]** > **[!UICONTROL Roles and Permissions]**&#x200B;并添加新角色。
1. 使用`bin/magento dev:que:enab`启用[!UICONTROL dev]查询日志。
1. 现在发送以下[!DNL GraphQL]请求（ID是[!UICONTROL base64]编码角色ID）：

   <pre><code>
   mutation {
   updateCompanyRole(
      input: {
         id: "Mg=="
         permissions: [
         "Magento_Company::view"
         "Magento_Company::view_account"
         "Magento_Company::user_management"
         "Magento_Company::roles_view"
        ]
      }
    ) {
      role {
         id

         name

         permissions {
         id

         text

         children {
            id

            text

            children {
               id

               text
             }
           }
         }
       }
     }
   }
   </code></pre>

1. 检查查询日志。
1. 您可以看到上述查询已执行。 此查询在`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`中执行。

<u>预期的结果</u>：

`app/code/Magento/CompanyGraphQl/Model/Company/Role/ValidateRole.php::validateResources`需要优化，以避免加载&#x200B;**[!UICONTROL company_permissions]**&#x200B;数据库表中所有可用的数据。

<u>实际结果</u>：

Adobe Commerce执行查询而不使用任何筛选器。 当记录数量很大时，Adobe Commerce需要大量时间来准备数据收集。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
