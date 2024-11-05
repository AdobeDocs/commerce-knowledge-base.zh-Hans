---
title: 在2.4.6升级之前减少过期的“oauth_tokens”
description: 当您在“oauth_token”表中看到大量“oauth_tokens”时，可能会导致升级到版本2.4.6时出现长时间延迟，本文提供了这个问题的解决方案。建议使用CleanExpiredTokens.php减少“oauth_token”表。
feature: Variables, Upgrade
role: Developer
exl-id: 92d1d15a-04da-4ba4-b6b8-5c491af9c4c1
source-git-commit: 1fa5ba91a788351c7a7ce8bc0e826f05c5d98de5
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 在2.4.6升级之前减少过期的`oauth_tokens`

本文提供了一种解决方案，来解决您在`oauth_token`表中看到大量`oauth_tokens`的问题，这可能会导致升级到版本2.4.6时出现长时间延迟。建议使用[`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]作业减少`oauth_token`表以删除过期的令牌。

## 受影响的产品和版本

* Adobe Commerce 2.4.0 - 2.4.6，所有部署方法

## 问题

如果`oauth_token`表中有大量`oauth_tokens`，则可能会导致在升级到版本2.4.6时出现较长的延迟。

升级过程包括加密这些令牌以实现额外的安全层，并且一次仅完成100条记录。 如果令牌数量很大，这可能需要几个小时。

减少`oauth_token`表中的大量`oauth_tokens`可以防止在升级到版本2.4.6时出现长时间延迟。

## 解决方案

在开始升级之前，请首先确保[`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]作业正在运行。 它通过删除过期的`oauth_tokens`令牌来减小`oauth_token`表的大小，默认情况下应该已经启用。

要手动触发[`CleanExpiredTokens.php`](https://github.com/magento/magento2/blob/2.4.5-p2/app/code/Magento/Integration/Cron/CleanExpiredTokens.php) [!DNL cron]作业，请运行：
```bin/magento cron:run --group=default```

## 相关阅读

* Commerce配置参考指南中的[服务> [!DNL OAuth]](https://experienceleague.adobe.com/docs/commerce-admin/config/services/oauth.html)
* Adobe Developer指南中的[身份验证指南](https://developer.adobe.com/developer-console/docs/guides/authentication/)
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)
