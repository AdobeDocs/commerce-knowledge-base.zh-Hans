---
title: Adobe Commerce状态列缺少导出的产品CSV文件
description: 当您在包含已导出产品的CSV文件中找不到状态列时，本文提供了此问题的解决方案。
exl-id: 3cbe1e6c-fc73-4331-add7-1ebcb28a4580
feature: Data Import/Export, Products
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%
---
# Adobe Commerce状态列缺少导出的产品CSV文件

当您在包含导出产品的CSV文件中找不到状态列（即，指示产品是启用还是禁用）时，本文提供了此问题的解决方案。 产品的状态由[!UICONTROL product_online]列指示。

## 受影响的产品和版本

Adobe Commerce（所有部署方法）所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

在包含导出产品的CSV文件中找不到[!UICONTROL status]列。 因此，例如，您导出包含所有SKU的CSV及其状态，但表似乎缺少[!UICONTROL status]列。

<u>要再现的步骤：</u>

1. 在Adobe Commerce管理员中，选择&#x200B;**[!UICONTROL System]**，在&#x200B;**[!UICONTROL Data Transfer]**&#x200B;下选择&#x200B;**[!UICONTROL Export]**。
1. 在&#x200B;**[!UICONTROL Export Settings]**&#x200B;部分中，从&#x200B;**[!UICONTROL Entity Type]**&#x200B;下拉列表&#x200B;**[!UICONTROL Products]**&#x200B;中选择。
1. 搜索&#x200B;**[!UICONTROL status]**，列在&#x200B;**[!UICONTROL Attribute Code]**&#x200B;下。 您会在可用属性(**[!UICONTROL Enable Product]**)列表中看到该属性代码。
1. 单击&#x200B;**[!UICONTROL Export]**。

<u>预期结果：</u>

在刚刚导出的CSV文件中，您看到一个标记为[!UICONTROL status]的列。

<u>实际结果：</u>

在导出的csv文件中看不到标记为[!UICONTROL status]的列。

## 原因

已在CSV文件中重命名产品的状态属性。 它现在是[!UICONTROL product_online]列。

## 解决方案

1. 选择&#x200B;**[!UICONTROL System]**，在&#x200B;**[!UICONTROL Data Transfer]**&#x200B;下选择&#x200B;**[!UICONTROL Import]**。
1. 单击&#x200B;**[!UICONTROL Download Sample File]**。
1. 您可以在CSV文件中看到[!UICONTROL product_online]列。

## 相关阅读

* 在我们的用户指南中[使用CSV文件](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/data-transfer/data-csv)。
* 我们用户指南中的[产品导出属性引用](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/data-transfer/data-attributes-product)。
