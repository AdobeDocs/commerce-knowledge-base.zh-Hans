---
title: Commerce管理员中的已锁定（灰显）字段
description: 本文为无法修改Commerce管理员中的字段提供了解决方案。
exl-id: 5fe0967a-4241-440b-bb0d-429fa5644bbc
feature: Admin Workspace
role: Developer
source-git-commit: bc800397a3c0c3a86eb717db60e445e13b299688
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Commerce管理员中的已锁定（灰显）字段

本文为无法修改Commerce管理员中锁定（灰显）字段的情况提供了解决方案。

## 受影响的产品和版本

* Adobe Commerce内部部署2.3.x、2.4.x
* 云基础架构上的Adobe Commerce 2.3.x、2.4.x

## 问题

将配置的更改保存到`app/etc/env.php`或`app/etc/config.php`后，便无法在管理员中修改设置。

<u>重现步骤</u>：

注意：以上是一个示例 — 该问题可能会影响已保存的所有配置。

1. 商家在终端中使用以下命令保存其投放方法凭据： `./vendor/bin/ece-tools config:dump`。 这会将凭据保存在`app/etc/env.php`文件中。
1. 然后，商家尝试稍后更改凭据。

<u>预期的结果</u>：

商家可以在“管理员”字段设置中设置值并保存它们。

<u>实际结果</u>：

管理员中的字段被锁定，或者值可以更改，但不会保存在管理员中。

## 原因

当配置保存到`env.php`或`config.php`时，您将无法在管理员中修改设置。 要允许编辑设置，您必须从`env.php`或`config.php`中删除配置。

## 解决方案

确保该配置尚未保存到`app/etc/env.php`或`app/etc/config.php`。 如果已保存，请尝试以下步骤：

* `config.php` — 删除设置，然后重新部署。
* `env.php` — 直接在服务器上修改此设置并删除设置，然后运行`bin/magento app:config:import`。

## 相关阅读

* [导出开发人员文档中的配置](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-export.html#sensitive-or-system-specific-settings)。
* 在我们的开发人员文档中[设置配置值](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-config-mgmt-set.html#config-cli-config-set)。
* 云基础架构上的[Adobe Commerce：通过我们的支持知识库中的配置管理](/help/how-to/general/magento-cloud-reduce-deployment-downtime-with-configuration-management.md)，减少部署停机时间。
