---
title: '在Adobe Commerce上更新编辑器失败：参数类型不兼容'
description: 本文为因代码编译问题而卡住部署的情况提供了解决方案。 此问题是由新版本的symfony/控制台依赖项(4.4.27、4.4.28)引起的。
exl-id: ba2dd229-29f6-43e2-9467-8bd1bf59e6ef
feature: Console
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 在Adobe Commerce上更新编辑器失败：参数类型不兼容

>[!NOTE]
>
>此问题现在已在最新的Symfony版本4.4.29版本中修复。

本文为因代码编译问题而卡住部署的情况提供了解决方案。 此问题是由新版本的symfony/控制台依赖项(4.4.27、4.4.28)引起的。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）和Magento Open Source：
   * 2.4.0、2.4.0-p1、2.4.1、2.4.1-p1、2.4.2、2.4.2-p1、2.4.2-p2、2.4.3
   * 2.3.5、2.3.5-p1、2.3.5-p2、2.3.6、2.3.6-p1、2.3.7、2.3.7-p1
* symfony/控制台依赖项(4.4.27、4.4.28)。

## 问题

新版本的symfony/控制台依赖项(4.4.27、4.4.28)正在导致依赖项编译过程失败。

<u>重现步骤</u>：

安装或升级Adobe Commerce或运行编辑器更新时，执行失败并显示以下错误消息：
*不兼容的参数类型：必需类型： int。 实际类型：字符串*

## 原因

该问题是由于Adobe Commerce核心代码与4.4.27和4.4.28版中发布的最新“symfony/console”依赖项不兼容造成的。

## 解决方案

在发布新的symfony/console版本4.2.29（预计于2021年8月发布）后，将自动解决此问题。

**如何在Adobe Commerce内部部署上修复：**

Adobe Commerce内部部署2.4.x

在CLI/终端中运行以下命令：

``composer require symfony/console:">=4.4.0 <4.4.27 || ~4.4.29"``

所有2.3.5及更高版本的Adobe Commerce本地商家都应运行以下CLI命令：

``composer require symfony/console:"~4.1.0||~4.2.0||~4.3.0||>=4.4.0 <4.4.27 || ~4.4.29"``

**如何在云基础架构上修复Adobe Commerce：**

运行上述命令或升级到欧洲经委会工具的最新版本(ece-tools：2002.1.7)，该版本将于7月29日星期四提供。 有关步骤，请参阅我们的开发人员文档中的[Cloud for Adobe Commerce >更新ece-tools版本](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)。

完整的修复将在Adobe Commerce（所有部署方法）2.4.4中发布。

## 相关阅读

* Github： [2021-07-27编辑器更新不兼容的参数类型：必需类型： int。 实际类型：字符串](https://github.com/magento/magento2/issues/33595)
