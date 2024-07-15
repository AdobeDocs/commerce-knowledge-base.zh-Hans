---
title: 'PWA Studio：浏览器显示“无法代理到”错误'
description: 本主题讨论当Web浏览器显示“*无法代理到*”并且控制台显示
exl-id: de689633-34b8-4a25-bbd0-a58742c4d03c
feature: Console
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# PWA Studio：浏览器显示“无法代理到”错误

本主题讨论当Web浏览器显示“*无法代理到*”并且控制台显示

```
ENOTFOUND
```

使用Progressive Web App (PWA) Studio for Adobe Commerce时出错。

## 受影响的产品和版本

* Adobe CommercePWA Studio

## 问题

<u>要再现的步骤</u>：

* 在浏览器中加载Adobe Commerce store 。

<u>预期的结果</u>：

* Adobe Commerce存储区会在您的浏览器中正常加载。

<u>实际结果</u>：

* 您的Web浏览器显示“*无法代理到*”错误，控制台显示如下错误：

```
    ENOTFOUND
```


## 原因

NodeJS无法解析Adobe Commerce存储的主机名。

## 解决方案

1. 确保您的Adobe Commerce商店在多个Web浏览器中加载。
1. 如果您运行的是本地DNS服务器或VPN，请向您的主机文件（位于`/etc/hosts`）添加一个条目，并手动映射此域（[有关主机文件编辑](https://linuxize.com/post/how-to-edit-your-hosts-file/)的通用说明），以便NodeJS可以解析它。

## 相关阅读

* [PWA StudioAdobe Commerce文档](https://magento.github.io/pwa-studio/)
* [工具和库](https://magento.github.io/pwa-studio/technologies/tools-libraries/)
