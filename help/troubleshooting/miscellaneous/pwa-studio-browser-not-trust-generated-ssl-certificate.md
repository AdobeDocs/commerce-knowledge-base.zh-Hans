---
title: 'PWA Studio：浏览器不信任生成的SSL证书'
description: 本文提供了一种解决方案，可在开发期间导航到PWA Studio店面的本地实例时，解决浏览器中不受信任的、生成的SSL证书警告。
exl-id: b7bfe1e6-5832-4472-9e51-f04b8583428a
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# PWA Studio：浏览器不信任生成的SSL证书

本文提供了一种解决方案，可在开发期间导航到PWA Studio店面的本地实例时，解决浏览器中不受信任的、生成的SSL证书警告。

## 受影响的产品和版本

Adobe CommercePWA Studio

## 问题

浏览器不信任您本地PWA Studio店面生成的SSL证书。

## 原因

浏览到开发/暂存站点。

## 解决方案

在您的店面项目中，运行命令以向本地开发实例添加自定义主机名和SSL证书：

```sh
yarn buildpack create-custom-origin ./
```

生成证书由[devcert](https://github.com/davewasmer/devcert)处理。 它依赖于OpenSSL，因此使用以下命令确保您的系统上有openssl的当前版本：

`openssl version`

版本应为1.0或更高版本（对于OSX High Sierra，则为LibreSSL 2）。

您可以在OSX上安装[Homebrew](https://brew.sh/)的OpenSSL较高版本，在Windows上安装[Chocolatey](https://chocolatey.org/)，或者安装Linux分发的包管理器。

如果您正在运行Linux，请确保您的系统上安装了`libnss3-tools`（或等效项）。 [devcert](https://github.com/davewasmer/devcert#skipcertutil)自述文件的此部分提供了详细信息。

一些用户建议删除devcert文件夹以触发证书重新生成。

* 对于MacOS用户，此文件夹通常位于： `{{~/Library/Application Support/devcert }}`
* 对于Windows用户，此文件夹通常位于： `${User}\AppData\Local\devcert`

## 我们的支持知识库中的相关阅读

* [PWA Studio：自签名证书信任错误](https://support.magento.com/hc/en-us/articles/360038973172)
* [PWA Studio：Webpack在开始编译前挂起](/help/troubleshooting/miscellaneous/pwa-studio-webpack-hangs-before-beginning-compilation.md)
* [PWA Studio：浏览器显示“无法代理到”错误](/help/troubleshooting/miscellaneous/pwa-studio-browser-displays-cannot-proxy-to-error.md)
* [PWA Studio：运行开发人员模式时出现验证错误](/help/troubleshooting/miscellaneous/pwa-studio-validation-errors-when-running-developer-mode.md)
