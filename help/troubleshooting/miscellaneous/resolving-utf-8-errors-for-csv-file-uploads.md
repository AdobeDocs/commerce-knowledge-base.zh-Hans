---
title: 解决CSV文件上传的UTF-8错误
description: 本文修复了您收到错误消息“CSV文件必须使用UTF-8编码”的问题。 此错误消息表示您尝试上传的文件包含非法字符或不允许使用的字符。 虽然UTF-8编码允许[大多数字符](https://www.fileformat.info/info/charset/UTF-8/list.htm)，但某些编码与MagentoBI不兼容。
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# 解决CSV文件上传的UTF-8错误

本文修复了您收到错误消息“CSV文件必须使用UTF-8编码”的问题。 此错误消息表示您尝试上传的文件包含非法字符或不允许使用的字符。 虽然UTF-8编码允许[大多数字符](https://www.fileformat.info/info/charset/UTF-8/list.htm)，但某些字符与MagentoBI不兼容。

要解决此问题，您需要更改文件的编码。 使用正确的编码重新保存文件通常可以解决此问题，但请注意，在执行此操作时，您可能会丢失一些信息（例如，可能会丢弃非法字符）。

我们建议使用[Sublime Text](https://www.sublimetext.com/2)保存并编码该文件。

1. 在Microsoft Excel、Google文档、Apple编号或您选择的项目中打开您的文件。
1. 单击&#x200B; &#x200B;**文件** > **另存为**&#x200B; &#x200B;并选择&#x200B; &#x200B;**逗号分隔值(.csv)**&#x200B;格式以保存文件。
1. 以高级文本打开CSV文件。
1. 在高级文本中，导航到&#x200B;**文件** > **&#x200B;使用编码保存** > **UTF-8\*{&#x200B;5}。**&#x200B;这将以UTF-8编码保存CSV文件。    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [将数据](https://docs.magento.com/mbi/data-analyst/importing-data/connecting-data/using-file-uploader.html)(在我们的Magento指南中)上载到BI中的新表。
