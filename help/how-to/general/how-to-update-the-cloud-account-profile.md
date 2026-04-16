---
title: 如何更新云帐户配置文件
description: 本文介绍了在云帐户上修改用户档案的步骤。
feature: Cloud, Support
role: Admin, Developer
exl-id: b0c9dbcf-9745-494d-a662-80c5c6378068
source-git-commit: bc8dbb1b43c3f2ad8f2ac214fd303f6a4d3e3412
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# 如何更新云帐户配置文件

本文介绍了如何在云帐户上修改用户档案的步骤。

## 解决方案

在云帐户上修改用户档案时，可以修改以下字段：

1. [!UICONTROL First name]
1. [!UICONTROL Last name]
1. [!UICONTROL Username]

   >[!NOTE]
   >
   >更新Cloud Console用户名会将项目URL从`https://console.adobecommerce.com <old-username>/<project-id>`更改为`https://console.adobecommerce.com/<new-username>/<project-id>`。
   >
   >更新后，使用旧URL的链接不再有效。 团队成员必须更新已保存的书签、内部文档和任何自动化内容才能使用新URL。
   >
   >此更改仅适用于新的Cloud Console URL。 旧版项目URL (`https://<region>.magento.cloud/projects/<project-id>`)未使用该用户名，并且无需更改即可继续使用。

要修改这些字段，请执行以下步骤：

1. 通过[Adobe帐户登录](https://accounts.magento.cloud)访问您的帐户。
1. 单击&#x200B;**[!UICONTROL Account Settings]**&#x200B;选项卡。
1. 选中&#x200B;*创建新密码*&#x200B;复选框。
1. 进行必要的更改，然后单击&#x200B;*保存*。

>[!NOTE]
>
>您的密码不会更改。

## 哪些内容不能修改？

1. **[!UICONTROL Password]**：
若要更改密码，请访问[Adobe密码重置](https://account.adobe.com/)，因为此配置文件已链接至您的帐户/电子邮件地址。

1. **[!UICONTROL Email Address]**：
修改此字段取决于您的具体情况。

如果您需要将当前帐户的所有权转让给新所有者或其他电子邮件地址，则需要更新与该帐户关联的主要用户电子邮件。

请参阅：[https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-transfer.html?lang=en)
