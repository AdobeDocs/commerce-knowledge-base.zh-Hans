---
title: 在管理员中批量删除期间，删除的产品比启动的产品多
description: 本文为云基础架构2.2.3上的已知AdobeсOmmerce提供了一个修补程序，该问题与在Commerce Admin的网格中执行批量删除时未选择删除记录有关。
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# 在管理员中批量删除期间，删除的产品比启动的产品多

本文为云基础架构2.2.3上的已知AdobeсOmmerce提供了一个修补程序，该问题与在Commerce Admin的网格中执行批量删除时未选择删除记录有关。

## 问题

在“管理员”中，如果您选择要删除的客户或客户记录，筛选网格，然后选择&#x200B;**删除**&#x200B;操作，则会删除所有记录。

<u>重现步骤</u>：

1. 在管理员中导航到&#x200B;**目录** > **产品**。
1. 选择一个或多个产品。
1. 从“操作”下拉菜单中选择“删除”。

<u>预期的结果</u>：

仅删除选定的产品。

<u>实际结果</u>：

某些其他产品也被删除。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-10600\_EE\_2.2.3\_v1.composer.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.3

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce内部部署2.1.8-2.1.14、2.2.0-2.2.2和2.2.4-2.2.5
* 云基础架构上的Adobe Commerce 2.2.4 - 2.2.5

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
