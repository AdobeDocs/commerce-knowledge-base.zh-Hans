---
title: 'Adobe Commerce 2.4.2 B2B：电子邮件模板未更新电子邮件'
description: 本文介绍了一个已知的Adobe Commerce 2.4.2 B2B问题，该问题导致更新电子邮件模板中的某些信息时没有在电子邮件中更新。 此问题会影响电子邮件内容，如客户信息、汇率、货币符号、电子邮件模板更改等。 目前没有可用的解决方案，但本文底部提供了解决方法。
exl-id: 31b7086f-a941-4682-aa07-301ac31d543b
feature: B2B, Communications
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Adobe Commerce 2.4.2 B2B：电子邮件模板未更新电子邮件

本文介绍了一个已知的Adobe Commerce 2.4.2 B2B问题，该问题导致更新电子邮件模板中的某些信息时没有在电子邮件中更新。 此问题会影响电子邮件内容，如客户信息、汇率、货币符号、电子邮件模板更改等。 目前没有可用的解决方案，但本文底部提供了解决方法。

## 受影响的产品和版本

* Adobe Commerce内部部署2.4.2
* Adobe Commerce cloud基础架构2.4.2
* B2B 1.3.1

## 问题

<u>重现步骤</u>：

1. 公司管理员在前端创建一个PO（采购订单）。
1. 检查自动批准的电子邮件。 **客户名称** / **货币汇率**&#x200B;应为预期值。
1. 在客户帐户页面上的管理员和公司管理员名称中更改货币符号（**商店>配置>货币设置>货币选项**）。
1. 客户管理员在管理员中创建另一个PO。
1. 检查自动批准的电子邮件。

<u>预期结果：</u>

客户名称和货币符号在电子邮件中发生更改，并且新值符合预期。

<u>实际结果</u>：

客户名称和货币符号在电子邮件中不发生更改，而是具有其以前的值。

## 解决方法

手动运行cron作业或使用者以传播新信息。

## 相关阅读

* 在我们的开发人员文档中[管理消息队列](https://devdocs.magento.com/guides/v2.4/config-guide/mq/manage-message-queues.html)。
