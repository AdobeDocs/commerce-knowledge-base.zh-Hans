---
title: 不在pub media目录中执行的自定义服务器端脚本
description: 本文修复了将自定义服务器端脚本放置在'中时未执行的问题。云基础架构上Adobe Commerce应用程序的/pub/media/'目录。 这是预期的安全限制，因为'。/pub/media/'目录可写。 要使脚本可执行，请将脚本置于不可写目录（如'）中。/app/code/”或'。/pub/'。
exl-id: fcad8a5d-47d6-4729-93a4-2410d7710d69
feature: Media
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# 不在pub media目录中执行的自定义服务器端脚本

本文修复了将自定义服务器端脚本放置在云基础架构上Adobe Commerce应用程序的`./pub/media/`目录中时未执行的情况。 这是预期的安全限制，因为`./pub/media/`目录可写。 若要使脚本可执行，请将脚本放在不可写入的目录中，如`./app/code/`或`./pub/`。

## 受影响的版本

* 云基础架构上的Adobe Commerce：2.1.x及更高版本，Starter和Pro规划架构、翼和旧式架构

## 问题：脚本未执行

启动时无法执行自定义服务器端脚本。

例如，当最终用户(Adobe Commerce购物者)单击指向带有脚本的`\*.php`文件的链接(如&#x200B;*domain.com/media/directory/script.php* )时，将下载脚本而不是执行脚本。

## 原因：脚本文件的位置不正确

当脚本文件位于云基础架构上的Adobe Commerce应用程序的`./pub/media/`目录中时，会出现问题。 这是预期行为：由于安全限制，从不执行来自可写目录(`./pub/media/`)的文件。

## 解决方案：将脚本放在不可写目录中

将服务器端脚本存储在不可写入的目录中，如`./app/code/`或`./pub/`

## 相关文档

* 在开发人员文档中，[Adobe Commerce云>项目结构>可写目录](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/file-structure#writable-directories)。
