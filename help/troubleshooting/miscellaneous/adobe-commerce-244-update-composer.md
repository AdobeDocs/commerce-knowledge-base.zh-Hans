---
title: 升级到Adobe Commerce 2.4.4时，出现编辑器插件问题
description: 本文提供了一个解决方案，可避免在从Adobe Commerce 2.4.3及更早版本升级到Adobe Commerce 2.4.4或更高版本时（在发布未来版本时）出现composer插件问题。
exl-id: 7502ca9e-c307-4e8a-aa1d-4886e7be25da
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# 升级到Adobe Commerce 2.4.4时，出现编辑器插件问题

本文提供了一个解决方案，可避免在从Adobe Commerce 2.4.3及更早版本升级到Adobe Commerce 2.4.4或更高版本时（在发布未来版本时）出现编辑器插件问题。

## 受影响的产品和版本

* Adobe Commerce本地，更新到2.4.4或更高版本时的任何版本（发布时）
* 云基础架构上的Adobe Commerce，更新到2.4.4或更高版本时的任何版本（发布时）
* Magento Open Source，更新到2.4.4或更高版本时的任何版本（发布时）

## 问题

在2022年7月之后更新到Adobe Commerce 2.4.4或更高版本时，您可能会收到来自编辑器的有关插件的警告。

<u>重现问题的步骤</u>：

先决条件：已安装Adobe Commerce 2.4.3或更低版本。

1. 按照中的说明开始升级 [执行升级](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/implementation/perform-upgrade.html).
1. 运行 `composer update` 命令升级Adobe Commerce应用程序。

<u>预期结果</u>：

升级成功。

<u>实际结果</u>：

安装失败，并出现与以下内容类似的错误：

```bash
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 591 installs, 0 updates, 0 removals
  - Installing laminas/laminas-dependency-plugin (2.2.0): Extracting archive
laminas/laminas-dependency-plugin contains a Composer plugin which is currently not in your allow-plugins config. See https://getcomposer.org/allow-plugins
Do you trust "laminas/laminas-dependency-plugin" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
Plugin initialization failed (require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory), uninstalling plugin
  - Removing laminas/laminas-dependency-plugin (2.2.0)
    Install of laminas/laminas-dependency-plugin failed


  [ErrorException]
  require(app/etc/NonComposerComponentRegistration.php): failed to open stream: No such file or directory
```

## 原因

2022年7月之后，Composer更改 [`allow-plugins` option](https://getcomposer.org/doc/06-config.md#allow-plugins) 到 `{}` 除非允许，否则和插件将不再加载。

## 解决方案

将以下内容添加到您的 `composer.json` 文件，具体取决于您安装Adobe Commerce的方式：

* 如果项目已创建 [使用 `composer create-project` 命令](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html#get-the-metapackage)：

  ```json
  "config": {
      "allow-plugins": {
          "dealerdirect/phpcodesniffer-composer-installer": true,
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

* 如果项目是通过其他方式创建的，但没有 `"dealerdirect/phpcodesniffer-installer"` 在 `"require-dev"` 部分：

  ```json
  "config": {
      "allow-plugins": {
          "laminas/laminas-dependency-plugin": true,
          "magento/*": true
      }
  }
  ```

更新后 `composer.json` 文件，运行 `composer update` 命令并重新启动升级过程。
