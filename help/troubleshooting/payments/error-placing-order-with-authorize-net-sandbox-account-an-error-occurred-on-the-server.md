---
title: 使用Authorize.net Sandbox帐户下订单时出错（服务器上出现错误）
description: 本文修复了使用Authorize.Net Direct Post下订单时出现的“*服务器上发生错误*”错误消息。
exl-id: 764a550a-3373-483c-843d-d8c848dcee35
feature: Compliance, Console, Customer Service, Orders, Payments
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 使用Authorize.net Sandbox帐户下订单时出错（服务器上出现错误）

本文修复了使用Authorize.Net Direct Post下订单时出现的“*服务器*&#x200B;上发生错误”错误消息。

>[!WARNING]
>
>**弃用通知**
>
>由于支付服务指令[PSD2](https://docs.magento.com/user-guide/v2.3/stores/compliance-payment-services-directive.html)和许多API的不断演变，Authorize.Net有过时和将来不再符合安全性的风险。 因此，现已弃用，我们建议您在Adobe Commerce配置中禁用它，并过渡到相应的[Commerce Marketplace扩展](https://marketplace.magento.com/extensions.html)。
>
>**此集成已从Adobe Commerce 2.4.0版本中删除，已在2.3的当前版本中弃用。**
>
>有关从已弃用的付款集成进行安全过渡的详细信息，请参阅我们的[DevBlog](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Magento-core-payment-integrations/ba-p/426445)。

## 问题

使用[Authorize.Net Direct Post](https://docs.magento.com/user-guide/v2.3/payment/authorize-net-direct-post.html)沙盒帐户下订单会导致出现错误消息：

>>
“服务器上发生错误。 请尝试重新下单”

## 原因1：已启用测试模式

似乎不明显，但即使使用Sandbox帐户进行测试，Authorize.net的&#x200B;**测试模式**&#x200B;设置也必须设置为&#x200B;**No**。

## 解决方案1：禁用测试模式

1. 转到&#x200B;**商店** > **配置** > **销售** > **付款方式** > **其他付款方式** > **Authorize.net直接Post**。
1. 将&#x200B;**测试模式**&#x200B;设置为“否”（取消选中&#x200B;**使用系统值**，然后在菜单中选择“否”）。
1. 单击&#x200B;**保存配置**。

![authorize-net_test-mode_setting.png](/help/troubleshooting/miscellaneous/assets/authorize-net_test-mode_setting.png)

## 原因2：错误的URL

Authorize.net设置可能包含关键Authorize.Net资源的不正确URL地址。

## 解决方案2：提供正确的URL

* **网关URL：**   `https://test.authorize.net/gateway/transact.dll`
* **事务详细信息URL：**   `https://apitest.authorize.net/xml/v1/request.api`
* **API引用：**   `https://developer.authorize.net/api/reference/`

## 如果没有任何帮助：获取调试信息

如果通过Authorize.net下订单失败，出现非信息性&#x200B;*“出现错误”*&#x200B;错误，请检查Adobe Commerce `debug.log`。

### Transact.dll

如果`debug.log`为空，请检查Web浏览器控制台中的&#x200B;**transact.dll**&#x200B;响应：

1. 打开控制台。
1. 下订单前，转到&#x200B;**网络**&#x200B;选项卡并选择&#x200B;**保留日志**。    ![web-console_network_preserve-log.png](assets/web-console_network_preserve-log.png)
1. 通过&#x200B;**transact.dll**&#x200B;筛选响应，以查看可能错误的响应消息。    ![transact-dll_web-console_response.png](assets/transact-dll_web-console_response.png)
