---
title: 在浏览器中访问Adobe Commerce时，出现PHP版本错误或404错误
description: 本文提供了解决方案，来解决您无法在Web浏览器中访问Adobe Commerce实例并收到404错误或“不支持的PHP版本”错误的问题。
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 在浏览器中访问Adobe Commerce时，出现PHP版本错误或404错误

本文提供了解决方案，来解决您无法在Web浏览器中访问Adobe Commerce实例并收到404错误或“不支持的PHP版本”错误的问题。

## 受影响的产品和版本：

* Adobe Commerce 2.3.x

## 问题：不支持的PHP版本

当您尝试访问Adobe Commerce店面或Commerce管理员时，会显示以下消息：

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### 解决方案

尝试以下操作：

* 将PHP升级到版本7.3。有关详细信息，请参阅我们的开发人员文档中的[Adobe Commerce 2.3技术栈栈要求](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/system-requirements)。
* 重新启动Apache，因为它可能使用与文件系统上相同的PHP版本。 要重新启动Apache，请使用以下命令：
   * Ubuntu： `service apache2 restart`
   * CentOS： `service httpd restart`

## 问题：错误404

当您尝试访问Adobe Commerce店面或Commerce管理员时，显示404（未找到）错误。

### 解决方案

尝试以下操作：

* 确保启用[Apache服务器重写](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/web-server/apache)。 如果Apache Server重写设置不正确，则无法从正确的位置提供静态文件。
* 您在安装期间输入的基本URL可能存在问题。 从命令行安装Adobe Commerce时，将基本URL指定为`--base-url=`的值，或指定为Web安装程序“Web配置”页上的&#x200B;**商店地址**&#x200B;字段的值。 基本URL *必须*&#x200B;以方案（如`http://`）开头，并以尾随斜杠(/)结尾。 请使用有效值再次运行安装程序，然后尝试访问Adobe Commerce。
