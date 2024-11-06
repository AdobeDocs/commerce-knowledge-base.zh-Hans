---
title: 部署后.magento.env.yaml更改未显示在env.php中
description: 本文为部署后.magento.env.yaml文件中的更改未反映在app/etc/env.php中的问题提供了解决方案。
exl-id: 39ea7295-ba5a-40cc-bc68-a5e0b965c1a7
feature: Deploy
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# 部署后.magento.env.yaml更改未显示在env.php中

>[!NOTE]
>
>如果您遇到此问题，请升级到ece-tools 2002.1.5进行修复。 2002.1.5具有在每次部署时重置opcache的功能，因此无需更改设置`opcache.enable_cli=1`。 如果您不想升级，则必须按照解决方案中所述执行解决步骤。

本文为部署后`.magento.env.yaml`文件中的更改未反映在`app/etc/env.php`中的问题提供了解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce （所有[支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)）。

## 问题

在`.magento.env.yaml`文件中进行的更改不会影响生成的`app/etc/env.php`。

<u>要再现的步骤：</u>

更改`.magento.env.yaml`中的任何值并推送至服务器，服务器应定义当前签出的环境的配置（和部署设置）。 有关步骤，请参阅我们的开发人员文档中的[环境变量>部署变量](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy)。

<u>预期结果：</u>

在`.magento.env.yaml`文件中进行的更改会影响生成的`app/etc/env.php`。

<u>实际结果：</u>

这些更改对部署后的`app/etc/env.php`变量没有影响。

## 原因

问题可能是由于`php.ini`文件中`opcache.enable_cli`参数的值不正确导致的。

## 解决方案

1. 检查系统是否根据[Adobe Commerce性能最佳实践>软件建议](https://experienceleague.adobe.com/en/docs/commerce-operations/performance-best-practices/software)进行了配置。
1. 通过执行`php -i | grep opcache.enable_cli`检查`php.ini`中的`opcache.enable_cli`指令是否设置为`0`
1. 如果输出类似于`opcache.enable_cli=1`，请编辑项目根目录中的`php.ini`文件并将`opcache.enable_cli=1`更改为`opcache.enable_cli=0`
1. 重新部署项目。

## 相关阅读

* [Cloud for Adobe Commerce >生成和部署](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml)。
