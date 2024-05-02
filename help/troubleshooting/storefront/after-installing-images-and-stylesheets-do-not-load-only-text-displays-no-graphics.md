---
title: 安装后，不加载图像和样式表；只显示文本，不加载图形
description: 本文介绍了安装Adobe Commerce后样式表和图像未加载问题的可能原因和解决方案。
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# 安装后，不加载图像和样式表；只显示文本，不加载图形

本文介绍了安装Adobe Commerce后样式表和图像未加载问题的可能原因和解决方案。

## 受影响的产品和版本

* Adobe Commerce 2.2.x和2.3.x
* Magento Open Source2.2.x和2.3.x

## 问题

<u>重现问题的步骤</u>

1. 安装Adobe Commerce。
1. 导航到店面或管理员。

<u>预期结果</u>

应用样式后，没有UI元素看起来像是缺少样式。

<u>实际结果</u>

样式应用不正确，缺少图形。

## 原因

指向图像和样式表的路径不正确，可能是因为基础URL不正确，也可能是因为服务器重写(CentOS、Ubuntu)设置不正确。

要确认这种情况，请使用Web浏览器检查器检查静态资源的路径，并验证这些资源是否位于Adobe Commerce或Magento Open Source文件系统中。

静态资产位于 `<magento_root>/pub/static/` ，在 `frontend` 和 `adminhtml` 目录。

## 解决方案

根据您使用的软件以及问题的原因，以下是可采用的解决方案：

* 如果您使用的是Apache Web Server，请验证 [服务器重写](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) 设置和Adobe Commerce/Magento Open Source服务器的基本URL，然后重试。 如果您设置了Apache `AllowOverride` 指令不正确，未从正确的位置提供静态文件。
* 如果您使用的是nginx Web服务器，请确保 [配置虚拟主机文件](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). nginx虚拟主机文件必须满足以下条件：
   * 此 `include` 指令必须指向Adobe Commerce/Magento Open Source安装目录中的nginx配置文件示例。 例如：    `include /var/www/html/magento2/nginx.conf.sample;`
   * 此 `server_name` 指令必须与安装Adobe Commerce/Magento Open Source时指定的基本URL匹配。 例如： `server_name 192.186.33.10;`
* 如果应用程序位于 [生产模式](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode)，尝试使用部署静态视图文件 `magento setup:static-content:deploy` 命令。 有关部署静态文件的详细信息，请参阅 [部署静态视图文件](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) 在我们的开发人员文档中。
