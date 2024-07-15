---
title: 从2.4.4升级到2.4.4后，将包降级 — p1
description: 本文提供了一个修补程序，用于修复商家在2.4.4版上运行“composer update”命令时，以下列出的包（模块）将降级到与版本2.4.4不兼容并且只应该与版本2.4.5及更高版本一起使用的早期版本的问题。
exl-id: 4ebdbcd7-6905-4647-b071-1e4413455f38
feature: Upgrade
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# 从2.4.4升级到2.4.4后，将包降级 — p1

本文提供了一个修补程序，用于修复商家在版本2.4.4上运行`composer update`命令时，下面列出的包（模块）将降级到与版本2.4.4不兼容并且只应该与版本2.4.5及更高版本一起使用的早期版本的问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.4.4
* Adobe Commerce内部部署2.4.4
* Magento Open Source2.4.4

## 问题

在以下两种情况下，会发生此问题以及如何重现此问题：

### 场景1

<u>重现步骤</u>：

从2.4.4升级到2.4.4-p1时，有许多包（模块）会降级并产生类似的输出：

```text
Downgrading magento/module-adobe-ims (2.1.4 => 2.1.3)
Downgrading magento/module-adobe-ims-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-admin-ui (1.3.2 => 1.3.1)
Downgrading magento/module-adobe-stock-client-api (2.1.2 => 2.1.1)
Downgrading magento/module-adobe-stock-image (1.3.3 => 1.3.2)
Downgrading magento/module-adobe-stock-image-admin-ui (1.3.3 => 1.3.2)
Downgrading magento/module-banner-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-inventory (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-advanced-checkout (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-api (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-bundle-product (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-catalog-api (1.3.3 => 1.3.2)
Downgrading magento/module-inventory-configurable-product-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-configurable-product-frontend-ui (1.0.3 => 1.0.2)
Downgrading magento/module-inventory-import-export (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-in-store-pickup-admin-ui (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-frontend (1.1.3 => 1.1.2)
Downgrading magento/module-inventory-in-store-pickup-graph-ql (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-in-store-pickup-sales-admin-ui (1.1.3 => 1.1.2-p1)
Downgrading magento/module-inventory-in-store-pickup-shipping (1.1.2 => 1.1.1)
Downgrading magento/module-inventory-low-quantity-notification (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-low-quantity-notification-api (1.2.2 => 1.2.1-p1)
Downgrading magento/module-inventory-requisition-list (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-admin-ui (1.2.3 => 1.2.2)
Downgrading magento/module-inventory-sales-api (1.2.2 => 1.2.1)
Downgrading magento/module-inventory-shipping-admin-ui (1.2.3 => 1.2.2-p1)
Downgrading magento/module-inventory-source-selection-api (1.4.2 => 1.4.1-p1)
Downgrading magento/module-inventory-wishlist (1.0.2 => 1.0.1)
Downgrading magento/module-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-re-captcha-checkout-sales-rule (1.1.1 => 1.1.0)
Downgrading magento/module-re-captcha-customer (1.1.3 => 1.1.2)
Downgrading magento/module-re-captcha-frontend-ui (1.1.3 => 1.1.2)
Downgrading magento/module-staging-page-builder (2.2.3 => 2.2.2)
Downgrading magento/module-two-factor-auth (1.1.4 => 1.1.3)
Removing magento/module-admin-adobe-ims (100.4.0)
```

<u>预期的结果</u>：

从版本2.4.4升级到2.4.4-p1会生成版本2.4.4-p1的正确包（模块）。

<u>实际结果</u>：

从版本2.4.4升级到2.4.4-p1时，这些包的（模块）版本会降级，但这些消息可以忽略，并且功能不会受到影响。

### 场景2

<u>重现步骤</u>：

当2.4.4商家运行`composer update`命令时，上面&#x200B;**方案1**&#x200B;中列出的相同包（模块）将升级到其新版本，这些版本仅与版本2.4.5兼容，不应与版本2.4.4一起使用。

<u>预期的结果</u>：

从版本2.4.4升级到2.4.4-p1会生成版本2.4.4-p1的正确包（模块）。

<u>实际结果</u>：

从版本2.4.4升级到2.4.4-p1后，包（模块）将降级。

## 解决方法1：修补程序

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名或单击以下链接： [下载ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)

## 兼容的Adobe Commerce和Magento Open Source版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.4.4
* Adobe Commerce内部部署2.4.4
* Magento Open Source2.4.4

>[!NOTE]
>
>该修补程序与任何其他Adobe Commerce及Magento Open Source版本和版本不兼容。

## 如何应用修补程序

使用附加的bash脚本[ACPLTSRV-2017-fix.sh.zip](assets/ACPLTSRV-2017-fix.sh.zip)作为此问题的解决方法。

**有关如何使用脚本的确切说明：**

### 在云基础架构上的Adobe Commerce上：

1. 将bash脚本文件`ACPLTSRV-2017-fix.sh`下载到云代码库的本地签出项。
1. 运行bash脚本文件`ACPLTSRV-2017-fix.sh`以本地修改编辑器文件。
1. 将修改的编辑器文件添加并提交到Git存储库。

### 在Adobe Commerce或Magento Open Source内部部署：

1. 将bash脚本`ACPLTSRV-2017-fix.sh`放置在Adobe Commerce/Magento Open Source2.4.4安装的`root`文件夹中（与`composer.json`相同的文件夹）。
1. 运行带有`apply`参数的bash脚本以将受影响的包（模块）锁定到其2.4.4版本：

   ```bash
   sh ACPLTSRV-2017-fix.sh apply
   ```

1. 运行更新后的编辑器以安装锁定的包（模块）。
1. 准备好升级到2.4.5或2.4.4-p1后，使用`rollback`参数运行脚本：

   ```bash
   sh ACPLTSRV-2017-fix.sh rollback
   ```

   由于包（模块）要求冲突，跳过此步骤将导致升级错误。
1. 完成上述步骤后，即可开始升级。

## 解决方法2

此问题的第二个解决方法是不运行不带任何参数的`composer update`命令。
