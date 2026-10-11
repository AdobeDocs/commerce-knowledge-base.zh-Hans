---
title: 安装期间出现异常
description: 本文为使用Web安装向导安装Adobe Commerce时出现的问题提供了可能的解决方案。
exl-id: f9b8ba2d-c8bd-4020-9e95-7194cc51317c
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%
---
# 安装期间出现异常

本文为使用Web安装向导安装Adobe Commerce时出现的问题提供了可能的解决方案。

## 受影响的产品和版本

* Adobe Commerce（所有部署方法）2.2.x、2.3.x
* Magento Open Source 2.2.x和2.3.x

## 问题

安装期间会显示异常。 用户已报告各种异常，包括：

```bash
Module 'Magento_Indexer':
Running recurring..
[ERROR] exception 'Exception' with message 'Recoverable Error: Argument 1 passed to Magento\Indexer\Model\Config\Data::__construct() must be an instance of Magento\Framework\Indexer\Config\Reader, instance of Magento\Indexer\Model\Config\Reader given, called in /home/magento2_dev/
public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php on line 14 and defined in /home/magento2_dev/public_html/
app/code/Magento/Indexer/Model/Config/Data.php on line 22' in /home/magento2_dev/public_html/lib/internal/Magento/Framework/App/ErrorHandler.php:67
Stack trace:
#0 /home/magento2_dev/public_html/app/code/Magento/Indexer/Model/Config/Data.php(22): Magento\Framework\App\ErrorHandler->handler(4096,
'Argument 1 pass...', '/home/magento2...', 22, Array)
#1 /home/magento2_dev/public_html/generated/code/Magento/Indexer/Model/Config/Data/Interceptor.php(14): Magento\Indexer\Model\Config\Data->
__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config), Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')
#2 /home/magento2_dev/public_html/lib/internal/Magento/Framework/ObjectManager/Factory/AbstractFactory.php(103): Magento\Indexer\Model\Config\Data\Interceptor->__construct(Object(Magento\Indexer\Model\Config\Reader), Object(Magento\Framework\App\Cache\Type\Config),
Object(Magento\Indexer\Model\Resource\Indexer\State\Collection), 'indexer_config')

... more ...
```

## 解决方案

按如下方式清除`var`和`generated`下的`<magento_root>/generated/code`和其他目录：

```bash
rm -rf <magento_root>/generated/code/* <magento_root>/generated/metadata/* <magento_root>/var/cache/*
```

清除目录后，请重试安装。
