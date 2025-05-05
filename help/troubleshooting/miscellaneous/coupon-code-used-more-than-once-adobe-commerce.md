---
title: 单次使用优惠券多次，Adobe Commerce
description: 本文为购物车价格规则优惠券无法正常工作时的问题提供了解决方案。 商家会设置优惠券以供一次使用，并且客户可以多次使用。
exl-id: 9c81de40-65a3-422d-9053-3c894b863a0a
feature: Orders
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# 单次使用优惠券多次，Adobe Commerce

本文为购物车价格规则优惠券无法正常工作时的问题提供了解决方案。 商家会设置优惠券以供一次使用，并且客户可以多次使用。


## 受影响的产品和版本

Adobe Commerce（所有部署方法） 2.4.3及更高版本

## 问题

商家会设置优惠券以供一次使用，并且客户可以多次使用。

<u>重现步骤</u>：

1. 创建优惠券并将优惠券配置为单次使用。
1. 继续结帐。
1. 使用您刚刚创建的优惠券。
1. 再次进入结账流程，并使用相同的优惠券。

<u>预期的结果</u>：

优惠券只能使用一次。 显示一条消息： *优惠券代码“COUPON_NAME”无效*。

<u>实际结果</u>：

优惠券可以多次使用。


## 原因

商家未设置并运行`sales.rule.update.coupon.usage`消费者，从而导致不当行为。

## 解决方案

将`sales.rule.update.coupon.usage`使用者添加到`app/etc/env.php`文件。

```php
...
    'cron_consumers_runner' =>
    array [
        'cron_run' => true,
        'max_messages' => 20000,
        'consumers' =>
        array [
            'sales.rule.update.coupon.usage'
        ]
    ],
...
```

有关详细步骤，请参阅我们的开发人员文档中的[管理消息队列>配置](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/message-queues/manage-message-queues#configuration)。

## 相关阅读

在我们的开发人员文档中，[消息队列概述](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework)。
