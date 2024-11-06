---
title: 由于启用了维护模式，站点加载失败
description: “本文修复了由于保持启用维护模式或未自动禁用维护模式而导致站点无法加载的问题。 您可能会收到一条错误消息： *服务暂时不可用由于维护停机或容量问题，服务器暂时无法为您的请求提供服务。*”
exl-id: 77e01588-e135-4d24-a0c4-1a6ee123f4a8
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# 由于启用了维护模式，站点加载失败

本文修复了由于保持启用维护模式或未自动禁用维护模式而导致网站无法加载的问题。 您可能会收到一条错误消息： *服务暂时不可用由于维护停机或容量问题，服务器暂时无法为您的请求提供服务。*

## 受影响的版本和产品

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x

## 问题

维护模式是部署过程的一部分。 但是，如果该模式已自动启用且未被禁用，或者商家手动启用维护模式且忘记禁用，则可能会导致部署失败。

## 原因

启用维护模式会阻止站点加载。

## 解决方案

要检查当前的维护模式状态，请从CLI运行以下命令：

```
bin/magento maintenance:status
```

要禁用维护模式，请在CLI中运行以下命令：

```
bin/magento maintenance:disable
```

## 相关阅读

要了解何时使用维护模式，请参阅我们的开发人员文档中的[启用或禁用维护模式](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)。
