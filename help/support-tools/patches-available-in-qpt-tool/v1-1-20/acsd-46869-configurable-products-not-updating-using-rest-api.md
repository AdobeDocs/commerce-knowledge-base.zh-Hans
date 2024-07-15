---
title: 'ACSD-46869：可配置产品未在签出时使用REST API进行更新'
description: ACSD-46869修补程序修复了可配置产品在签出时未使用REST API进行更新的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20后，即可使用此修补程序。 修补程序ID为ACSD-46869。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
exl-id: d1bac489-f0f3-4b50-bc48-86c844230da7
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-46869：可配置产品未在签出时使用REST API进行更新

ACSD-46869修补程序修复了可配置产品在签出时未使用REST API进行更新的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-46869。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL QPT] 登陆页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在签出期间，不会使用REST API更新可配置产品。

<u>重现步骤</u>：

1. 创建具有颜色和大小属性的可配置产品。
1. 选择&#x200B;**[!UICONTROL Options]**&#x200B;并将产品添加到购物车。
1. 转到&#x200B;**[!UICONTROL Checkout]**，多次更新大小（数量除外），然后检查请求和响应。
1. 更新大小时，您会获得以下响应。

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>预期的结果</u>：

根据更改更新值。

<u>实际结果</u>：

`option_value`未更新，因此下订单时，其大小值为旧值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tools] > Quality Patches Tool指南中的用法](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html)，检查您的Adobe Commerce问题是否有可用的修补程序。

有关[!DNL QPT]中其他可用修补程序的信息，请参阅Quality Patches Tool指南中的 [!DNL QPT]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中的[Patches。
