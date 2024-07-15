---
title: “B2B：公司无法访问店面上的个人资料页面”
description: 本文为已知的Adobe Commerce 2.2.4 B2B问题提供了一个修补程序，该问题与注册公司在店面的“帐户”页面上收到错误有关。
exl-id: 5f0d81a2-e0a1-487b-8a4f-28b8cb704e32
feature: B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# B2B：公司无法访问店面的配置文件页面

本文为已知的Adobe Commerce 2.2.4 B2B问题提供了一个修补程序，该问题与注册公司在店面的“帐户”页面上收到错误有关。

## 问题

客户（公司）可以在网站上成功创建公司帐户，但收到&#x200B;*“没有客户ID = &quot;* and *&quot;您还没有公司帐户&quot;*&#x200B;错误消息。 他们尝试访问公司配置文件页面时也可能收到&#x200B;*“500内部服务器错误”*。

## Patch

要下载带有修补程序的归档文件，请单击以下链接：

[下载MDVA-9013\_EE\_2.2.2\_composer.patch](assets/MDVA-9013_EE_2.2.2_composer.patch.zip)

### 兼容的Adobe Commerce版本

该修补程序是为以下对象创建的：

* Adobe Commerce内部部署2.2.2

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* 从2.2.0到2.2.4的云基础架构上的Adobe Commerce
* 从2.2.0到2.2.1以及从2.2.3到2.2.4的Adobe Commerce内部部署

## 如何应用修补程序

有关说明，请参阅[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。
