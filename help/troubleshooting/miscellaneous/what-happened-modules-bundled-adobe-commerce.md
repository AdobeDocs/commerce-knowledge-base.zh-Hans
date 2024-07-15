---
title: Adobe Commerce 2.4.4中缺少模块
description: 当2.4.4中不存在以前Adobe Commerce版本中包含的模块时，本文提供了此问题的解决方案。
exl-id: c0335b66-803b-44d7-b966-7d60a5f21d8d
feature: Extensions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Adobe Commerce 2.4.4中缺少模块

当2.4.4中不存在以前Adobe Commerce版本中包含的模块时，本文会提供相应的解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 问题

您无法安装第三方模块，或者在升级到Adobe Commerce 2.4.4时发现某些核心捆绑扩展不存在。仅当安装的第三方模块需要从Adobe Commerce 2.4.4中删除某个捆绑的扩展时，或者如果项目利用了其中一个已删除模块的某些功能时，才应发生这种情况。

* 情景1：项目已利用核心捆绑模块的功能之一。 Adobe Commerce 2.4.4中不包括已使用的捆绑模块。成功升级到Adobe Commerce 2.4.4后，您意识到缺少该模块及其提供的功能。

* 情景2：您的当前项目中安装了一个模块，该模块依赖于其中一个已移除的捆绑模块。

这是预期行为，因为供应商捆绑的扩展已从Adobe Commerce 2.4.4代码库中移除。

## 解决方案

单独安装/购买官方扩展。 这些在[Commerce Marketplace](https://marketplace.magento.com/extensions.html)上可用。

## 相关阅读

Adobe Commerce文档>发行信息> Adobe Commerce 2.4.4发行说明中的[供应商捆绑的扩展](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-4.html?#vendor-bundled-extensions)。
