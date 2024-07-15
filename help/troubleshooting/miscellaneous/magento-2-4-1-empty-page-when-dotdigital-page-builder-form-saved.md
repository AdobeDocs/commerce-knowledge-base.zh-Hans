---
title: 'Adobe Commerce 2.4.1：保存dotdigital Page Builder表单时显示空页面'
description: 本文为Adobe Commerce 2.4.1中的已知问题提供了解决方法，即在使用Safari浏览器时，在“管理面板”中保存dotdigital Page Builder表单后显示空网页。
exl-id: 682eac73-1ad2-4093-acfb-6a8da4c05cf5
feature: Page Builder
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Adobe Commerce 2.4.1：保存dotdigital Page Builder表单时显示空页面

本文为Adobe Commerce 2.4.1中的已知问题提供了解决方法，即在使用Safari浏览器时，在“管理面板”中保存dotdigital Page Builder表单后显示空网页。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.1
* 云基础架构上的Adobe Commerce 2.4.1

## 问题

<u>重现步骤</u>

1. 转到&#x200B;**管理员面板** > **内容** > **页面**，然后选择任何页面的&#x200B;**编辑**。
1. 转到&#x200B;**内容**&#x200B;并单击&#x200B;**使用页面生成器编辑**&#x200B;按钮。
1. 拖动&#x200B;**dotdigital form**&#x200B;块并选择&#x200B;**编辑**。
1. 选择一个测试表单，然后选择&#x200B;**嵌入式**&#x200B;模式并保存该表单。
1. 保存页面修改。

<u>预期结果：</u>

该网页应已成功保存。

<u>实际结果：</u>

网页为空。 重新加载网页后，将应用更改。

## 解决方法

解决方法是使用Safari的替代浏览器。 此问题计划于2021年第1季度在下一个版本Adobe Commerce 2.4.2中修复。

## 相关阅读

* [什么是页面生成器？](https://devdocs.magento.com/page-builder/docs/)位于我们的开发人员文档中。
* 在开发人员文档中[页面生成器设置](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/setup.html)。
* 我们用户指南中的[页面生成器](https://docs.magento.com/user-guide/cms/page-builder.html)。
* 用户指南中的[页面生成器 — 元素](https://docs.magento.com/user-guide/cms/page-builder-elements.html)。
