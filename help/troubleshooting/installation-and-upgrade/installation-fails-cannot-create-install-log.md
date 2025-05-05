---
title: 安装失败；无法创建install.log
description: 本文修复了由于安装向导在安装期间未创建“install.log”而导致安装失败的问题。
exl-id: ff614018-8e49-4170-a806-8ebdc91ae8a9
feature: Install, Logs, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 安装失败；无法创建install.log

本文修复了由于安装向导在安装期间未创建`install.log`而导致安装失败的问题。

## 问题

同时运行Adobe Commerce进程可能会导致创建安装日志时出现问题。 （例如，将两个不同的安装放在不同的选项卡页面中。）

## 原因

Installation-fails-cannot-create-install.log
在`php.ini`中查看`open_basedir`的设置。 安装向导使用[sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP调用获取临时目录的值。 如果[open\_basedir](http://php.net/manual/en/ini.core.php#ini.open-basedir)设置为拒绝连接到`sys_get_temp_dir`指定的目录，则安装失败。
在`php.ini`中查看`open_basedir`的设置。 安装向导使用[sys\_get\_temp\_dir ( void )](https://php.net/manual/en/function.sys-get-temp-dir.php) PHP调用获取临时目录的值。 如果[open\_basedir](https://php.net/manual/en/ini.core.php#ini.open-basedir)设置为拒绝连接到`sys_get_temp_dir`指定的目录，则安装失败。


## 解决方案

要解决此问题，请更改`open_basedir`的值并重新启动Web服务器。

如果不确定如何更改此值，请执行以下步骤：

1. 如果尚未这样做，请创建[phpinfo.php](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/optional-software)。
1. 在浏览器的地址或位置字段中输入以下URL： `https://<your web server IP or hostname>/<path to docroot>/phpinfo.php`
1. 查找`php.ini`的位置。     在显示的结果中，`php.ini`通常被指定为&#x200B;**加载的配置文件**。
1. 以具有根权限的用户身份，在文本编辑器中打开`php.ini`。
1. 找到`open_basedir`的值并更改它。
1. 将更改保存到`php.ini`。
1. 重新启动Web服务器。
