---
title: 应用修补程序将导致您的网站停机
description: 本文讨论您刚刚应用的修补程序导致网站中断的问题。 要解决此问题，可以删除修补程序。
exl-id: dc765bcd-0761-4efd-a345-46a908d61272
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# 应用修补程序将导致您的网站停机

本文讨论您刚刚应用的修补程序导致网站中断的问题。 要解决此问题，可以删除修补程序。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法），所有受支持的版本
* Magento Open Source，所有版本

## 问题

应用修补程序后，您的站点将关闭。

## 原因

出现此问题的原因可能是，您刚才应用于网站的修补程序、自定义项、过去应用的其他修补程序之间的版本不兼容，或者出现其他错误。

## 解决方案

删除修补程序。 对于云基础架构上的Adobe Commerce，修补程序删除方法与Adobe Commerce内部部署和Magento Open Source方法不同。

### Magento Open Source，所有1.X版本

对于Magento Open Source1.X版本，

* 运行以下SSH命令： `h SUPEE_patch --revert `

### Adobe Commerce内部部署、Magento Open Source，所有2.x版本

对于Adobe Commerce内部部署和Magento Open Source2.x版本，

1. 运行以下SSH命令：

   ```
   patch -p1 -R %patch_name%.composer.patch
   ```

   （如果上述命令不起作用，请尝试使用`-p2`而不是`-p1`）

1. 要使更改生效，请在&#x200B;**系统** > **缓存管理**&#x200B;下的管理员中刷新缓存。

### 云基础架构上的Adobe Commerce，所有版本

对于云基础架构上的Adobe Commerce，所有版本，

1. 从`m2-hotfixes`目录中删除`%patch_name%.composer.patch`文件。
1. 提交并推送代码更改：

   ```
   git commit -m "Remove %patch_name%.composer.patch patch" && git push origin
   ```

## 相关阅读

* [如何应用我们的支持知识库中Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
