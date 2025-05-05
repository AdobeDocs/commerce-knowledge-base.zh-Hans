---
title: 在云基础架构上的Adobe Commerce上更改管理员URL
description: 默认情况下，[Commerce管理员](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/admin/admin) URL设置为*&amp；lt；domain_name&amp；gt；/admin*。 本文介绍如何更改URL。
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 在云基础架构上的Adobe Commerce上更改管理员URL

默认情况下，[Commerce管理员](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html?lang=zh-Hans) URL设置为&#x200B;*&lt;域\_名称>/管理员*。 本文介绍如何更改URL。

## 方法1：使用“管理员”进行更改

请阅读我们的用户指南中的步骤：[使用自定义管理员URL >更改管理员](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=zh-Hans#use-a-custom-admin-url)。

## 方法2：添加ADMIN\_URL环境变量

### 集成环境

从[Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hans)，添加新的变量，其包含：

**名称：** ADMIN\_URL **值：**&#x200B;新管理员URL

* 有关详细步骤，请参阅我们的开发人员文档中的[添加环境变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=zh-Hans#configure-environment)。
* 另请参阅我们的开发人员文档中的[环境变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=zh-Hans)。

### 当暂存和生产在Cloud Console中不可用时

[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)，请求为您的暂存或生产环境添加ADMIN\_URL变量。

如果可从Cloud Console访问暂存和生产环境，请按照上面&#x200B;*集成环境*&#x200B;部分中所述添加环境变量。

### 使用Cloud CLI添加变量

您可以使用以下Cloud CLI命令（对于main）添加ADMIN\_URL变量：

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

有关更多详细说明，请参阅《Commerce on Cloud Infrastructure指南》中管理员变量主题中的[更改管理员URL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=zh-Hans#change-the-admin-url)。

请注意，使用Cloud CLI更改ADMIN\_URL变量会触发环境的重新部署。 变量在默认情况下是可继承的；要阻止继承，请使用Cloud CLI命令选项来指示您不希望子环境继承变量值。 请参阅《云基础架构上的Commerce指南》中变量级别的[可见性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=zh-Hans#visibility)主题。
