---
title: 适用于Adobe Commerce的Magento Order Management System (OMS)处理错误
description: 当您在Magento Order Management System (OMS) for Adobe Commerce中运行“bin/magento oms：messages：process”的CLI中收到“getMode()”错误时，本文提供了此问题的解决方案。
exl-id: 83089465-f810-4a3b-bdb6-4720b44f0b49
feature: System
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%
---
# 适用于Adobe Commerce的Magento Order Management System (OMS)处理错误

当您在适用于Adobe Commerce的Magento Order Management System (OMS)中运行`bin/magento oms:messages:process`的CLI中出现`getMode()`错误时，本文提供了此问题的解决方案。

## 受影响的产品和版本

使用MCOM连接器3.1.1和3.2.0版时，会出现此错误。 在MCOM Connector 3.3.0中可解决此问题。 它不是特定于MDC或MOM版本。

## 问题

在CLI中运行以下命令时：

`bin/magento oms:messages:process`

CLI中输出类似于以下内容的错误消息：

```
<project-id>@<project-id>:~$ php bin/magento oms:messages:process

Processing messages...

PHP Fatal error:Uncaught Error: Call to a member function getMode()
on null in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php:64

Stack trace:

  #0 [internal function]: Magento\InventoryMessageBus\Handler\OnAggregateStockUpdatedSubscriber->onUpdated(Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #1 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(81):
  call_user_func(Array, Object(Magento\InventoryMessageBus\Model\Event\OnAggregateStockUpdated))

  #2 [internal function]: Magento\ServiceBus\Message\SingleMessageProcessor->Magento\ServiceBus\Message\\{closure}(Array)

  #3 /app/<project-id>/vendor/magento/module-service-bus/Message/SingleMessageProcessor.php(86):
  array_map(Object(Closure), Array)

  #4 /app/<project-id>/vendor/magento/module-service-bus/Message/Processor.php(110):
  Magento\ServiceBus\Message\SingleMessageProcessor->process(Object(Magento\CommonMessageBus\Message\Message))

  #5 /app/t in /app/<project-id>/vendor/magento/module-inventory-message-bus/Handler/OnAggregateStockUpdatedSubscriber.php
  on line 64
```

## 原因

Ï
当连接器尝试处理`magento.inventory.source_management`条消息时，会发生这种情况。 连接器尝试处理这些消息，就像它们是`magento.inventory.source_stock_management.update`消息一样，需要模式值。 由于`magento.inventory.source_mangement`消息中没有模式，因此出现此错误。

## 解决方案

要解决此问题，请在CLI中运行以下[!DNL SQL]语句，该语句将删除`mcom_api_messages`表中的所有记录：

`delete from mcom_api_messages;`

## 相关阅读

* OMS文档[OMS连接器安装教程](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/setup-tutorial/)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
