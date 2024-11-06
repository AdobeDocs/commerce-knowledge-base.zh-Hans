---
title: 云上的Adobe Commerce存在变量/导出文件夹权限问题
description: 解决由于服务器“var/export/email”文件夹中的文件权限问题而无法导出产品数据的问题，本文提供了解决方案。 症状包括产品和目录导出在用户界面中不可用，但在使用SSH时可见。
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 云上的Adobe Commerce存在变量/导出文件夹权限问题

本文为由于`var/export/email`文件夹中服务器上的文件权限问题而无法导出产品数据的问题提供了解决方案。 症状包括产品和目录导出在用户界面中不可用，但在使用SSH时可见。

## 受影响的产品和版本

云基础架构上的Adobe Commerce，2.3.0-2.3.7-p2、2.4.0-2.4.3-p1

## 问题

无法导出`var/export/email`或`var/export/archive`文件夹中的文件。
由于`var/export/email`或`var/export/email/archive`的权限，部署失败，因为该存档文件夹是在电子邮件下创建的，如果我只是执行导出/电子邮件，有时仍然有问题)，无法将内容添加到子文件夹`var/export/email/archive`的帐户。

<u>重现步骤</u>：

在管理员中，转到&#x200B;**系统** > *数据传输* > **导出**。
选择要保存在`var/export/`文件夹中的CSV文件。

<u>预期的结果</u>：

CSV文件可见，并且可以导出。

<u>实际结果</u>：

CSV文件不可见。 您还会看到权限被拒绝消息： *RecursiveDirectoryIterator：：__construct(/app/project id>/var/export/email)：无法打开目录：权限被拒绝*

对于所有导出类型，您都会收到相同的消息：“高级定价”、“客户财务”、“客户主文件”和“客户地址”。

## 原因

这是由于在`/var`内创建的具有不完美权限的文件夹所导致： `d-wxrwsr-T`。 T粘性位表示用户只能删除他们拥有的文件，而缺少可执行文件则表示他们无法在目录中创建文件。

当系统创建名为`export`的文件夹时，经常会注意到这种情况，该文件夹包含名为`email`的文件夹，该文件夹包含名为`archive`的文件夹。

要检查目录是否具有这些配置错误的权限，请在CLI/终端中运行以下命令：

`ls -ld var/export/`

如果权限配置错误，输出将为：

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## 解决方案

要解决此问题，请运行以下命令，将文件夹的权限更新为777 ，然后递归更新所有文件：

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## 相关阅读

* 用户指南中的[导出](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-export)。
