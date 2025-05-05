---
title: 安装或升级期间出现内存不足错误
description: 本文介绍了在安装/升级Adobe Commerce内部部署和Magento Open Source内部部署产品时出现的内存不足错误解决方案。
exl-id: c0ed8228-9357-4a3b-a102-1119386ea52a
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# 安装或升级期间出现内存不足错误

本文介绍了在安装/升级Adobe Commerce内部部署和Magento Open Source内部部署产品时出现的内存不足错误解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署2.3.x
* Magento Open Source内部部署2.3.x

## 问题

使用Web设置向导安装或更新Adobe Commerce或Magento Open Source应用程序或组件（如扩展、主题或语言包）时，会显示与以下内容类似的错误：

```bash
Could not complete update {"components":[
{"name":"magento/module-bundle-sample-data","version":"100.1.0"}
]} successfully: proc_open(): fork failed - Cannot allocate memory
```

错误

```bash
proc_open(): fork failed - Cannot allocate memory
```

还可以在命令行上显示。

## 解决方案 {#solution}

我们建议您[在我们的开发人员文档中为PHP](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/installation-guide/prerequisites/php-settings)分配2GB的内存，以确保您的安装或升级成功。

如果您已经这样做，请在您的计算机上创建一个交换文件。 如果Linux计算机需要更多内存资源并且RAM已满，则它使用&#x200B;*交换空间*。 交换空间用于内存中的非活动页。

以下只是建议；其他选项可能可用。 在继续之前，请咨询网络管理员或其他知识丰富的资源。 您必须运行命令以具有`root`权限的用户身份创建交换文件。

### 在Ubuntu上交换文件 {#swap-file-on-ubuntu}

使用下列参考中所述的`fallocate`命令：

* [如何在Ubuntu 14.04 (Digitalocean)上添加交换](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
* [如何在Ubuntu 16.04 (Digitalocean)上添加交换空间](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)
* [SwapFaq (help.ubuntu.com)](https://help.ubuntu.com/community/SwapFaq)

### 在CentOS上交换文件 {#swap-file-on-centos}

使用下列参考中所述的`mkswap`命令：

* [如何在CentOS 6 (Digitalocean)中添加交换](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-6)
* [如何在CentOS 7 (Digitalocean)中添加交换](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-centos-7)
* [交换空间（RedHat客户门户）](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ch-swapspace.html)
