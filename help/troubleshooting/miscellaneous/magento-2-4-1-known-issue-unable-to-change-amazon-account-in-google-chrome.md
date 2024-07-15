---
title: 'Adobe Commerce 2.4.1问题：无法在Chrome中更改Amazon帐户'
description: 本文介绍了一个已知的Adobe Commerce 2.4.1问题，其中客户在结账期间使用Amazon Pay登录之前使用的Amazon帐户，而不是建议登录。
exl-id: 8acffe99-b3ec-4b45-9434-61b66e963838
feature: Customer Service
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Adobe Commerce 2.4.1问题：无法在Chrome中更改Amazon帐户

本文介绍了一个已知的Adobe Commerce 2.4.1问题，其中客户在结账期间使用Amazon Pay登录之前使用的Amazon帐户，而不是建议登录。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.1
* 云基础架构上的Adobe Commerce 2.4.1

## 问题

在结账期间使用Amazon Pay时，客户会登录到以前使用的Amazon帐户，而不是被建议登录。

<u>要再现的步骤：</u>

1. 在店面，将任何物品添加到购物车并继续执行访客结账。
1. 单击&#x200B;**Amazon Pay**&#x200B;按钮。 Amazon.com登录弹出窗口。
1. 登录到Amazon帐户。
1. 选择地址并单击&#x200B;**下一步**。
1. 选择付款方式。
1. 单击&#x200B;**下订单**。
1. 返回主页并登录到商店帐户。
1. 再次将任何项目添加到购物车并继续结帐。
1. 单击&#x200B;**Amazon Pay**&#x200B;按钮。

<u>实际结果：</u>

您将再次自动登录到以前使用的（步骤3） Amazon帐户。

<u>预期结果：</u>

Amazon.com登录弹出窗口，您可以登录或为Amazon Pay创建新帐户。

## 原因

在以下情况之一中，可能会发生问题：

* 当`SameSite` Cookie值为`LAX`时，该Cookie将不会作为任何第三方调用的一部分发送。
* Mozilla Firefox内容阻止功能可阻止使用脚本和客户端存储机制，从而阻止第三方跟踪浏览器用户的活动。 Firefox使用外部供应商Disconnect.me提供要阻止的跟踪站点的列表。 Amazon Pay使用第三方网站上的iframe在登录后返回访问令牌，并渲染地址和钱包小组件。 借助内容阻止功能，Amazon Pay iframe加载请求被视为第三方跟踪请求并被阻止，导致购买者无法继续结账。
* 浏览器明确阻止第三方Cookie或JS的任何情况。

## 解决方案

确保浏览器不会阻止Amazon Pay iframe请求。
