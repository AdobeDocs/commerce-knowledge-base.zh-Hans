---
title: “[!DNL Live Search]显示缺货产品，而不管管理员中的库存状态设置如何”
description: 本文提供有关产品列表页面(PLP)显示*我们找不到与所选内容匹配的产品*错误，而搜索弹出窗口返回某些项目的已知问题的信息。
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# 无论管理员中的库存状态设置如何，[!DNL Live Search]都会显示缺货产品

>[!IMPORTANT]
>
>已在[[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html)中修复此问题。 要安装最新版本，请参阅用户指南中的[更新 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update)。

本文提供了有关产品列表页面(PLP)显示&#x200B;*无法找到与所选内容匹配的产品*&#x200B;错误，而搜索弹出框返回某些项目的已知问题的信息。

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.x

## 问题

[!DNL Live Search]显示搜索结果，而不考虑Adobe Commerce管理员中的库存状态设置。 即使&#x200B;**[!UICONTROL Display Out-of-Stock Products]**&#x200B;设置为&#x200B;*否*，也会显示产品。 它导致PLP错误&#x200B;*找不到与选择*&#x200B;匹配的产品。

<u>重现步骤</u>：

1. 创建类别、添加产品。 （示例：类别= _牛仔裤_，产品1 = _蓝色牛仔裤_，产品2 = _黑色牛仔裤_）
1. 使类别中的所有产品缺货。
1. 将&#x200B;**[!UICONTROL Display Out-of-Stock Products]**&#x200B;设置为&#x200B;*否*。
1. 在店面，在搜索字段中输入&#x200B;*牛仔裤*。
1. 在弹出窗口中单击&#x200B;**[!UICONTROL View All]**。

<u>预期的结果</u>：

您看到&#x200B;*在PLP上找不到与所选内容*&#x200B;匹配的产品，并且搜索弹出窗口中未显示任何产品。

<u>实际结果</u>：

您看到&#x200B;*在PLP上找不到与所选内容*&#x200B;匹配的产品，并且这两个产品都显示在搜索弹出窗口中。

## 解决方案

目前此问题无解决方法。 我们的[!DNL Live Search]团队很快将提供设置，以配置[!DNL Live Search]以正确显示产品。

## 相关阅读

在我们的用户指南中[安装 [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html)。
