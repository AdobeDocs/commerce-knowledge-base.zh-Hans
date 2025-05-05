---
title: 不显示图库图像，Adobe Commerce和Magento Open Source2.3.7-p2
description: 本文为上传到文件系统目录“pub/media”或“pub/media/catalog”的Adobe库图像未显示在Media Gallery UI中的问题提供了解决方案。 这是因为图像位于允许的媒体集目录之外。 对于这些要显示的图像，商家需要删除文件系统上的图像，然后重新上传到允许的媒体集目录中。
exl-id: 84488d87-095f-4739-858f-19a52d6e5822
feature: Categories, Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# 不显示图库图像，Adobe Commerce和Magento Open Source2.3.7-p2

本文为上载到文件Adobe目录`pub/media`或`pub/media/catalog`的媒体库图像未显示在媒体集UI中的问题提供了解决方案。 这是因为图像位于允许的媒体集目录之外。 对于这些要显示的图像，商家需要删除文件系统上的图像，然后重新上传到允许的媒体集目录中。

## 受影响的产品和版本

* Adobe Commerce和Magento Open Source2.3.7-p2


## 问题

商家可以将Adobe Stock图像上传到媒体集中的存储根，但这些图像未出现在UI中，并且看起来好像未上传一样。 这是因为系统注意到图像已上传到文件系统，尽管它在媒体集UI中不可用。 这意味着，一旦商家将图像上传到`pub/media`或`pub/media/catalog`，他们将无法使用该图像，直到该图像直接在文件系统中被删除。

<u>重现步骤</u>

1. 使用有效的API密钥启用Adobe Stock。
1. 打开媒体集（**目录** > **类别** > **内容**&#x200B;部分>单击&#x200B;**从媒体集选择**）。
1. 单击&#x200B;**搜索Adobe Stock**。
1. 选择图像。 单击&#x200B;**保存预览**。 请注意，您可能必须重置Adobe Stock网格才能显示图像。

<u>预期的结果</u>：

此时将显示图像。

<u>实际结果</u>：

显示错误消息： *找不到图像。 我们在媒体集中找不到此图像。*

## 原因

可以通过Adobe Stock将图像上传到媒体集存储根。

## 解决方案

在上传Adobe Stock图像之前，请选择媒体集存储根目录的任何子目录（不包括&#x200B;**存储根** > **目录**）。
从Adobe Commerce文件系统上的`pub/media`和`pub/media/catalog`文件夹中删除已上传的Adobe Stock图像，并将图像上传到任何允许的媒体集存储根子目录中（不包括&#x200B;**存储根** > **目录**）。

## 相关阅读

* 用户指南中的[媒体存储](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/content-design/wysiwyg/storage/media-storage)。
