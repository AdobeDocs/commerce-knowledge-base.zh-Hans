---
title: 从服务器电子邮件地址订购发送的电子邮件
description: 本文为云基础架构2.2.4中已知的Adobe Commerce问题提供了一个修补程序，该问题与从服务器电子邮件地址发送的订购电子邮件有关。
exl-id: f32e0c09-e19e-4269-bbba-0533d74a7f49
feature: Communications
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 从服务器电子邮件地址订购发送的电子邮件

本文为云基础架构2.2.4中已知的Adobe Commerce问题提供了一个修补程序，该问题与从服务器电子邮件地址发送的订购电子邮件有关。

## 问题

订单确认电子邮件从Apache Server电子邮件地址发送。 从配置的电子邮件地址发送其他电子邮件（忘记密码等）。

<u>重现步骤</u>：

1. 在选中&#x200B;**发送订单确认**&#x200B;框的情况下下订单。
1. 检查电子邮件。

<u>预期的结果</u>：

电子邮件是从Adobe Commerce配置的发送地址发送的。

<u>实际结果</u>：

该电子邮件是从正在使用的Apache Server中配置的电子邮件地址发送的。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-10993\_EE\_2.2.4\_v1.composer.patch](assets/MDVA-10993_EE_2.2.4_v1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.4

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Cloud基础架构上的Adobe Commerce 2.2.5
* Cloud基础架构上的Adobe Commerce 2.2.6
* 云基础架构上的Adobe Commerce 2.2.7
* Cloud基础架构上的Adobe Commerce 2.2.8
* Adobe Commerce内部部署2.2.4
* Adobe Commerce内部部署2.2.5
* Adobe Commerce内部部署2.2.6
* Adobe Commerce内部部署2.2.7
* Adobe Commerce内部部署2.2.8
* Adobe Commerce内部部署2.3.0

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
