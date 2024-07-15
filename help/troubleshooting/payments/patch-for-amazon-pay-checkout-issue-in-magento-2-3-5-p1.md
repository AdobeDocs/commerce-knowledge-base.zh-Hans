---
title: Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序
description: 该修补程序解决了在Adobe Commerce中使用Amazon Pay结帐时，无法从支付构件更改“审核和支付”步骤的支付方法的问题。
exl-id: a241f67f-019c-4ff2-a5ad-e7dc71639768
feature: Checkout, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Adobe Commerce 2.3.5-p1中有关Amazon Pay签出问题的修补程序

该修补程序解决了在Adobe Commerce中使用Amazon Pay结帐时，无法从支付构件更改“审核和支付”步骤的支付方法的问题。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce版本2.3.5-p1
* Adobe Commerce内部部署版本2.3.5-p1

## 问题

当购物者使用Amazon Pay结账、登录、进入支付步骤并尝试从支付构件更改其支付信用卡时，会显示一条错误消息。 如果购物者忽略错误并继续结帐，则无法完成结帐。

要解决此问题并删除错误，我们已创建一个[修补程序](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)。

<u>重现步骤</u>：

1. 使用Amazon Pay开始结帐。
1. 以Amazon Pay客户身份登录。
1. 选择配送方式并继续付款步骤。
1. 尝试将信用卡更改为其他信用卡。

<u>预期结果</u>：选择其他信用卡作为付款方式，且未出现错误。

<u>实际结果</u>：出现错误消息： *“请与此商家联系以获得完成订单的帮助。”*

## 解决方案

[应用下面的修补程序](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载BUNDLE-2554\_EE\_2.3.5-p1.composer.patch](assets/BUNDLE-2554_EE_2.3.5-p1.composer.patch.zip)

### 兼容的Adobe Commerce版本：

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce版本2.3.5-p1
* Adobe Commerce内部部署版本2.3.5-p1

该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：

* Adobe Commerce on cloud基础架构版本2.3.5
* Adobe Commerce内部部署版本2.3.5

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
