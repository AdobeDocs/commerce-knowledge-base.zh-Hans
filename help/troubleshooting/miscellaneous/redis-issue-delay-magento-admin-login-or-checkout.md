---
title: Redis问题延迟Commerce管理员登录或签出
description: 修复了登录到Commerce管理员或打开签出页面导致滞后或超时（超过30秒）的问题。 将Redis用于会话存储时，会出现此问题。
exl-id: a91a7a51-7cc4-4910-a9de-3a212788663f
feature: Admin Workspace, Checkout, Orders, Services
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Redis问题延迟Commerce管理员登录或签出

修复了登录到Commerce管理员或打开签出页面导致滞后或超时（超过30秒）的问题。 将Redis用于会话存储时，会出现此问题。

**原因：**   [Github问题\#12385](https://github.com/magento/magento2/issues/12385)。

**解决方案：**&#x200B;更新至最新的Adobe Commerce修补程序以修复所有版本的Redis和特定版本的Adobe Commerce的这些问题。

## 受影响的版本和技术

* 云基础架构上的Adobe Commerce版本2.1.11 - 2.1.13和2.2.1
* Adobe Commerce内部部署版本2.1.11 - 2.1.13和2.2.1
* Redis，所有版本

如果您在Cloud Infrastructure版本[2.2.0](#h_64593789291526919876198)上使用Adobe Commerce，则可以使用解决方法。

## 问题

登录到Commerce管理员或继续进入结帐页面需要30秒以上的时间。

仅当用户会话存储在Redis中时才会发生这种情况。

## 原因

Adobe Commerce的会话锁定机制存在问题，在使用Redis进行会话存储时，该机制为某些操作添加了30秒的超时时间。 有关详细信息，请参阅[Github问题\#12385](https://github.com/magento/magento2/issues/12385)。

Adobe Commerce 2.1.14和2.2.2中已修复此问题。

## 解决方案：补丁或升级

### 解决方案1：应用修补程序并进行修复

要接收修补程序，请[提交请求修补程序的支持票证](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)。 在票证中，指定您的Adobe Commerce版本以及修补程序的相应参考编号：

* **2.1.11及更高版本：** MDVA-7835
* **2.2.1：** MDVA-8128

一般（与版本无关）参考号为MAGETOW-84289。

### 解决方案2：升级到2.1.14/2.2.2或更高版本

如果您之前已考虑升级到Adobe Commerce 2.2.2或更高版本，则可以使用此更新机会来解决问题。

## 解决方法：禁用会话锁定

要禁用会话锁定，请在`env.php`文件的Redis配置部分中将`disable_locking`设置为`1`：

```php
'session' =>
  array (
    'save' => 'redis',
    'redis' =>
    array (
      'host' => 'redis.internal',
      'port' => 6379,
      'database' => '0',
      'disable_locking' => '1'
    ),
  ),
```

此解决方案不会影响任何其他Adobe Commerce功能。

### 应用修补程序后还原解决方法

使用修补程序应用修补程序后，无需再提供解决方法，因此您可以还原修补程序（将`disable_locking`设置为`0`）。

## 云基础架构2.2.0上的Adobe Commerce：使用ECE-Tools v2002.0.8或更高版本 {#h_64593789291526919876198}

版本为2002.0.3 - 2002.0.7的[ECE-Tools](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)部署脚本包自动应用解决方法](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html)，将`disable_locking`设置为`1`。 [这将禁用Adobe Commerce 2.2.0的会话锁定机制，在该机制上不会出现初始问题。

如果您在云基础架构2.2.0上运行Adobe Commerce，请将ECE-Tools升级到v2002.0.8或更高版本。 您还可以考虑将您在云基础架构上的Adobe Commerce升级到2.2.2或更高版本。
