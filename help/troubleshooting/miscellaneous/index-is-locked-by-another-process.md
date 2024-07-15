---
title: 索引被另一个进程锁定
description: 本文讨论了Adobe Commerce中的一个常见索引问题，该问题导致索引被其他进程锁定并跳过。
exl-id: 542c714c-fad5-4f0e-9757-d90044c36bfc
feature: Catalog Management, Categories
role: Developer
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# 索引被另一个进程锁定

本文讨论了Adobe Commerce中的一个常见索引问题，该问题导致索引被其他进程锁定并跳过。

## 受影响的产品和版本

* Adobe Commerce 2.X

## 问题

在CLI中进行完全重新索引时，Adobe Commerce会向您显示错误消息： *&#39;索引被另一个重新索引进程锁定。 正在跳过。*&#x200B;换句话说，当进程或索引类型被锁定时，您将无法重新索引该特定锁定的索引类型。 重新索引将始终跳过该索引类型。

## 原因

如果上一个索引未成功完成，则可能发生此错误。 可能的原因有：

* 该进程被另一个进程或用户中断。
* 内存限制。
* MySQL错误，如超时。
* 重新索引期间出现严重的PHP错误。

## 重现问题的步骤

1. 例如，假设    ```bash    cataloginventory_stock ```    索引类型已锁定。
1. 当您尝试通过运行CLI命令重新索引所有数据时    ```bash    php bin/magento indexer:reindex    ```，您将获得以下输出结果：    ```bash    customer_grid index has been rebuilt successfully in 00:00:09    catalog_category_product index has been rebuilt successfully in 00:00:07    catalog_product_category index has been rebuilt successfully in 00:00:00    catalogrule_rule index has been rebuilt successfully in 00:00:05    catalog_product_attribute index has been rebuilt successfully in 00:00:04    cataloginventory_stock index is locked by another reindex process. Skipping.    catalog_product_price index has been rebuilt successfully in 00:00:01    catalogrule_product has been rebuilt successfully in 00:00:00    catalogsearch_fulltext index has been rebuilt successfully in 00:00:01    ```
1. 如上所示，    ```bash    cataloginventory_stock```    已跳过索引过程。


## 解决方案

您需要重置索引状态，然后尝试运行新的重新索引过程。 对于重置索引状态，您需要运行以下命令：

```bash
bin/magento indexer:reset <index identifier>
```

如果不确定索引标识符（代码）是什么，可以使用命令列出它们：

```bash
bin/magento indexer:info
```

为了完整起见，下面提供了所有可能的本机索引组合：

```bash
bin/magento indexer:reset design_config_grid;
bin/magento indexer:reset customer_grid;
bin/magento indexer:reset catalog_category_product;
bin/magento indexer:reset catalog_product_category;
bin/magento indexer:reset catalogrule_rule;
bin/magento indexer:reset catalog_product_attribute;
bin/magento indexer:reset cataloginventory_stock;
bin/magento indexer:reset catalog_product_price;
bin/magento indexer:reset catalogrule_product;
bin/magento indexer:reset catalogsearch_fulltext;
```


## 相关阅读

在我们的支持知识库中：

* [Cron任务会锁定其他组的任务(云基础架构上的Adobe Commerce)](/help/troubleshooting/miscellaneous/cron-tasks-lock-tasks-from-other-groups.md)

在我们的用户指南中：

* [索引管理](https://docs.magento.com/user-guide/system/index-management.html?itm_source=merchdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=reindexing)

在我们的开发人员文档中：

* [索引概述](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexing.html)
* [索引器最佳实践](https://devdocs.magento.com/guides/v2.3/performance-best-practices/configuration.html#indexers)
* [配置并运行Cron](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-cron.html)
* [管理索引器](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands-index.html)
* [索引器优化](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/indexer-batch.html)
