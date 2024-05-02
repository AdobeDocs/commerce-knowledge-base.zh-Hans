---
title: ’[!DNL B2B] 在Adobe Commerce 2.4.6-p1 on-premises上安装1.4.0失败
description: 本文提供Adobe Commerce 2.4.6-p1内部部署问题的解决方法，其中 [!DNL B2B] 版本1.4.0安装失败。
feature: Install, Upgrade, B2B
role: Developer
exl-id: 4a557c13-7ec2-4cfe-b86e-bb0d1a441658
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# [!DNL B2B] 在Adobe Commerce 2.4.6-p1内部部署上，1.4.0安装失败

本文提供Adobe Commerce 2.4.6-p1内部部署问题的解决方法，其中 [!DNL B2B] 版本1.4.0安装失败。

## 受影响的产品和版本

* Adobe Commerce 2.4.6-p1 **内部部署**
* [!DNL B2B] 版本1.4.0

>[!NOTE]
>
>[!DNL B2B] 版本1.4.0成功安装在 **Adobe Commerce Cloud 2.4.6-p1**.

## 问题

<u>重现问题的步骤</u>：

1. 安装Adobe Commerce 2.4.6-p1。

   ```terminal
   m2install.sh -s composer --ee -v 2.4.6-p1
   ```

1. 尝试安装 [!DNL B2B] 版本1.4.0。

   ```terminal
   composer require magento/extension-b2b:1.4.0
   ```

<u>预期结果</u>：

[!DNL B2B] 版本1.4.0已成功在Adobe Commerce 2.4.6-p1上安装。

<u>实际结果</u>：

安装失败并出现以下错误：

```terminal
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
    - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.


Installation failed, reverting ./composer.json and ./composer.lock to their original content.
```

## 解决方法

已成功安装或升级到 [!DNL B2B] Adobe Commerce 2.4.6-p1上的1.4.0版，方法是为 [!DNL B2B] 带的安全包 [稳定性标记](https://getcomposer.org/doc/04-schema.md#package-links).

1. 从Adobe Commerce安装目录中，更新 `composer.json` 具有所需的依赖关系：

   ```terminal
   composer require magento/module-re-captcha-company=1.0.3-beta1@beta magento/security-package-b2b=1.0.4-beta1@beta
   ```

   **命令输出：**

   ```terminal
   Running composer update magento/module-re-captcha-company magento/security-package-b2b
   Loading composer repositories with package information
   Updating dependencies
   Lock file operations: 2 installs, 0 updates, 0 removals
     - Locking magento/module-re-captcha-company (1.0.3-beta1)
     - Locking magento/security-package-b2b (1.0.4-beta1)
   Writing lock file
   Installing dependencies from lock file (including require-dev)
   Package operations: 2 installs, 0 updates, 0 removals
     - Downloading magento/module-re-captcha-company (1.0.3-beta1)
     - Installing magento/module-re-captcha-company (1.0.3-beta1): Extracting archive
     - Installing magento/security-package-b2b (1.0.4-beta1)
   1 package suggestions were added by new dependencies, use `composer suggest` to see details.
   Package sebastian/phpcpd is abandoned, you should avoid using it. No replacement was suggested.
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. 更新 `composer.json` 添加 [!DNL B2B] 版本1.4.0。

   ```terminal
   composer require magento/extension-b2b=1.4.0
   ```

   **命令输出：**

   ```terminal
   ./composer.json has been updated
   Running composer update magento/extension-b2b
   Loading composer repositories with package information
   Updating dependencies
   ...
   Generating autoload files
   132 packages you are using are looking for funding.
   Use the `composer fund` command to find out more!
   No security vulnerability advisories found
   ```

1. 完成安装或升级过程。

   * [安装 [!DNL B2B] 在云基础架构上](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/b2b-module.html)
   * [安装内部部署](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html)
