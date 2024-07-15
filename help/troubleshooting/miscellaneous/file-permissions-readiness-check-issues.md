---
title: 文件权限准备情况检查问题
description: '本文修复了文件权限就绪检查问题。 Adobe Commerce文件系统中的目录必须可由Web服务器用户和Adobe Commerce文件系统所有者（如果适用）写入。 如果未正确设置您的权限，Web设置向导中会显示类似于以下内容的错误：'
exl-id: 252e6e7d-5269-44ce-b3ce-6fc2ea6a1c5c
feature: Roles/Permissions
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 文件权限准备情况检查问题

本文修复了文件权限就绪检查问题。 Adobe Commerce文件系统中的目录必须可由Web服务器用户和Adobe Commerce文件系统所有者（如果适用）写入。 如果未正确设置您的权限，Web设置向导中会显示类似于以下内容的错误：

![install_rc_file-perms.png](assets/install_rc_file-perms.png)

解决问题的方式取决于您设置的是单用户还是双用户：

* *一个用户*&#x200B;意味着您以同样运行Web服务器的相同用户身份登录到Adobe Commerce服务器。 此类设置在共享托管环境中很常见。
* *两个用户*&#x200B;意味着您通常无法&#x200B;*作为Web服务器用户*&#x200B;登录或切换到该用户。 通常以一个用户身份登录，并以其他用户身份运行Web服务器。 这在私有托管中或您拥有自己的服务器时是典型的。

## 单用户分辨率

如果您具有命令行访问权限，则输入以下命令(假设`/var/www/html/magento2`中安装了Adobe Commerce)：

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+w {} + && chmod u+x bin/magento
```

如果您没有命令行访问权限，请使用托管提供商提供的FTP客户端或文件管理器应用程序来设置权限。

## 双用户分辨率

要选择在一行中输入所有命令，请输入以下内容(假设Adobe Commerce安装在`/var/www/html/magento2`中，且Web服务器组名称为`apache`)：

```bash
$ cd /var/www/html/magento2 && find var vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

如果文件系统权限设置不正确且无法由Adobe Commerce文件系统所有者更改，则可以作为具有`root`权限的用户输入命令：

```bash
$ cd /var/www/html/magento2 && sudo find var vendor
  pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find
  var vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + &&
  sudo chown -R :apache . && sudo chmod u+x bin/magento
```
