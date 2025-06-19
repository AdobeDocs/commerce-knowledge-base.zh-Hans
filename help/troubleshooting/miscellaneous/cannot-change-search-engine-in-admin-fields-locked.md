---
title: 无法更改“app/etc/env.php”中的搜索引擎
description: 本文解决了一个问题：您尝试在Commerce管理员中更改搜索引擎，但字段被锁定。
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: 129e24366aedb132adb84e1f0196d2536422180f
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# 无法更改`app/etc/env.php`中的搜索引擎

本文提供了这个问题的解决方案，即您尝试从`app/etc/env.php`文件中删除搜索引擎配置，但在重新部署后，该配置将恢复为以前的设置或默认情况下更改为[!DNL OpenSearch]。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce，[所有支持的版本](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## 问题

您尝试在Commerce管理员中更改搜索引擎，但字段被锁定。

## 原因

在`app/etc/env.php`文件中锁定了搜索引擎配置，或者在`.magento.env.yaml`文件中明确定义了搜索引擎。

## 解决方案

1. 检查部署阶段下的`.magento.env.yaml`文件，并查看是否已配置`SEARCH_CONFIGURATION`变量。 示例：

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. `SEARCH_CONFIGURATION`变量是否存在吗？ 如果不存在，则默认情况下将搜索引擎配置锁定到[!DNL OpenSearch]。 要更改配置，必须将变量添加到具有搜索引擎相应值的`.magento.env.yaml`文件中。 如果`SEARCH_CONFIGURATION`变量存在并且您希望修改引擎，请在`.magento.env.yaml`中替换引擎的现有值。 可能/已知值： [!DNL opensearch]、[!DNL livesearch]、[!DNL elasticsuite]、[!DNL amasty_elastic]和[!DNL amasty_elastic_opensearch]。
1. 重新部署实例。
1. 管理员中的搜索引擎字段将保持锁定状态，但应该使用您指定的值更新该字段。

## 相关阅读

* 《Commerce on Cloud Infrastructure指南》中Commerce Admin[&#128279;](https://experienceleague.adobe.com/zh-hans/docs/experience-cloud-kcs/kbarticles/ka-26879)的锁定（灰色）字段。
