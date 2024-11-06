---
title: 清除Commerce Admin中的缓存时出错
description: '本文介绍如何在Commerce管理员中清除缓存时识别出现错误消息的原因。 当您尝试通过管理员清除缓存时，会收到以下消息：'
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# 清除Commerce Admin中的缓存时出错

本文说明如何在Commerce管理员中清除缓存时确定出现错误消息的原因。 当您尝试通过管理员清除缓存时，会收到以下消息：
无法删除*/app/project-id/pub/media/catalog/product/cache/directory/filename”文件。 警告！unlink(/app/project id/pub/media/catalog/product/cache/directory/filename)：没有这样的文件或目录*

## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.3.0-2.3.7、2.4.0-2.4.2-p1

## 问题

当您尝试通过管理员清除缓存时，会收到一条错误消息。

<u>要再现的步骤：</u>

1. 在管理员中，转到&#x200B;**系统** > **工具** > **缓存管理**。
1. 选择任何清除高速缓存选项。

<u>预期结果：</u>

您已成功刷新Adobe Commerce缓存，并且没有错误。

<u>实际结果：</u>

您收到“无法删除文件”错误。

## 原因

该错误与启动缓存清理操作与报告其完成之间的延迟有关。

## 解决方案

1. 确认错误中提到的文件在服务器上不存在（检查缓存清除是否成功）：

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

如果您看到以下输出：

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

操作完成时，尝试清除文件。 这不是一个错误；这是一个预计有时会发生的消息并发问题。 没有要诊断的问题。
但是，如果输出显示文件仍在缓存中，则需要[提交支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。

## 相关阅读

* 在我们的开发人员文档中[缓存管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management)。
