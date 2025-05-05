---
title: 由于编辑器中的更改，下载失败
description: 本文修复了Adobe Commerce下载失败和异常错误。
exl-id: 5abdab97-4b0c-466b-a68f-a2637d2826e5
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# 由于编辑器中的更改，下载失败

本文修复了Adobe Commerce下载失败和异常错误。

## 问题

下载期间显示以下错误：

```php
[ErrorException]
  file_get_contents(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## 原因

发生此情况是因为某些版本的Composer发生了更改。 解决方法是将编辑器降级为早期版本，然后再次尝试下载Adobe Commerce。

## 解决方案

在2015年11月21日至11月26日期间发行的任何版本Composer均存在此问题。 要确认此问题与Composer版本有关，请输入以下命令：

```php
composer -v
```

显示的版本类似于以下内容：

```php
Composer version 1.0-dev (2b14f0a047dd4f3545ec82381f65c36ea93a4c81) 2015-11-25 17:13:09
```

请注意，日期为2015-11-25，这表示Composer出现此问题。

要解决此问题：

1. 通过执行以下任一操作，更改Composer版本以允许您下载Adobe Commerce软件：

   * 使用以下命令降级编辑器： `composer self-update 1.0.0-alpha11`。
   * 将编辑器升级到2015年11月26日之前的版本： `composer self-update`。

1. 删除您的Adobe Commerce目录和子目录。
1. 请使用`[composer create-project](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/composer)`或`[git clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)`再次尝试下载。
1. 成功下载Adobe Commerce软件后，更新编辑器： `composer self-update`。
