---
title: PWA Studio：浏览器无法解析.local.pwadev站点
description: 本文提供了当其他程序或进程编辑了您的[主机文件] (https://en.wikipedia.org/wiki/Hosts_(file)并删除了您的项目域条目时的解决方案。
exl-id: a1606016-906a-433f-9e40-9faa5f9bd790
feature: Configuration
role: Developer
source-git-commit: 1d0d51209bdc02360c6f8527701cdf0da811659d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# PWA Studio：浏览器无法解析.local.pwadev站点

本文提供了当其他程序或进程编辑了您的[主机文件]&#x200B;(https://en.wikipedia.org/wiki/Hosts_(file\)并删除了您的项目域条目时的解决方案。

## 受影响的产品和版本

适用于Adobe Commerce的PWA Studio

## 问题

浏览到开发/暂存站点时，无法看到`.local.pwadev`站点。

## 原因

PWA Studio允许您为项目向本地计算机分配自定义主机名和SSL证书。 这涉及在计算机上类似`my-storefront-project-abc123.local.pwadev`的主机文件中创建一个新条目。

此条目可告知开发人员计算机上的任何浏览器在访问该URL时查看本地店面项目。 如果其他程序或进程进入并移除该条目，则浏览器将无法知道要转到何处，并且浏览器无法解析`.local.pwadev`站点。

## 解决方案

您可以[手动编辑主机文件](https://docs.rackspace.com/docs/modify-your-hosts-file)以将该条目添加回，但您应该检查其他已安装的软件，以查看覆盖先前更改的内容。

## 我们的支持知识库中的相关阅读

* [PWA Studio：自签名证书信任错误](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio：Webpack在开始编译之前挂起](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio：浏览器显示“无法代理到”错误](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio：运行开发人员模式时出现验证错误](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
