---
title: 启用广告阻止程序后未加载签出页面
description: 本文为cloud infrastructure 2.2.2上的已知Adobe Commerce提供了一个修补程序，该问题与uBlock或其他广告阻止程序导致无法加载签出页面有关。
exl-id: fe718f21-df23-4ab1-a6b0-03bad4d7095d
feature: Checkout, Orders
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# 启用广告阻止程序后未加载签出页面

本文为cloud infrastructure 2.2.2上的已知Adobe Commerce提供了一个修补程序，该问题与uBlock或其他广告阻止程序导致无法加载签出页面有关。

## 问题

如果为应用商店启用了Google Analytics，则当安装了uBlock或其他广告阻止程序的客户进行结账时，将阻止`trackingCode.js`文件加载，并且RequireJS会中断JS执行流程。 这会导致加载签出页面时出现问题。

<u>重现问题的步骤</u> ：

先决条件：必须在浏览器中安装并激活广告阻止程序。

1. 在Commerce管理员中，启用和配置Google Analytics功能。
1. 在店面打开产品页。
1. 将产品添加到购物车。
1. 单击&#x200B;**转到结帐**&#x200B;链接。

<u>预期结果</u>：已加载签出页面，客户可以完成签出。

<u>实际结果</u>：未加载签出页面；加载进度环永不消失。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-9353\_EE\_2.2.2\_v1.composer.patch](assets/MDVA-9353_EE_2.2.2_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.2

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 从2.1.0到2.1.14的云基础架构上的Adobe Commerce
* 云基础架构上的Adobe Commerce从2.2.0到2.2.1和2.2.3到2.2.5
* 从2.1.0到2.1.14的Adobe Commerce内部部署
* 从2.2.0到2.2.5的内部部署Adobe Commerce

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 有用的链接

* [GitHub上讨论的问题](https://github.com/magento/magento2/pull/13061)

## 附加文件
