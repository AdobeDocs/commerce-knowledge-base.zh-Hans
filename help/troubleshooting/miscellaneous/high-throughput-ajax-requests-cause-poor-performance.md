---
title: 高吞吐量AJAX请求导致性能不佳
description: 由于某些高吞吐量请求导致大量服务器负载和流量，因此本文为云基础架构站点上的Adobe Commerce内部部署或Adobe Commerce提供了性能问题解决方案。
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# 高吞吐量AJAX请求导致性能不佳

由于某些高吞吐量请求导致大量服务器负载和流量，因此本文为云基础架构站点上的Adobe Commerce内部部署或Adobe Commerce提供了性能问题解决方案。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.2.x、2.3.x
* Adobe Commerce内部部署2.2.x、2.3.x

>[!NOTE]
>
>已在云基础架构上的Adobe Commerce和内部部署的Adobe Commerce的2.3.4版本中修复了此问题。

### 问题

由于高吞吐量请求(如关键AJAX请求)，站点性能缓慢。

### 原因

高吞吐量AJAX请求包括与客户的私有内容相关的请求。

### 解决方案

有三种解决方案：

* [升级到版本2.3.4](https://devdocs.magento.com/cloud/project/project-upgrade.html). 如果当前无法执行此操作， [安装修补程序以修复问题](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* 确保减少请求（缓存请求或迁移到客户的私有内容）。
* 减少请求数。

<u>确保减少请求（缓存请求或迁移到客户的私有内容）</u>

如果在每个页面上触发了第三方AJAX请求，则尝试缓存这些请求或将其移至客户的专用内容。 商家可以通过确保使用GETHTTP方法调用自定义AJAX请求来实现这一点。 它将使这些请求能够被Fastly缓存。 如果有不应缓存的自定义AJAX请求，则应根据私有内容功能对其进行重构。 有关步骤，请参阅 [私有内容](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) 在我们的开发人员文档中。

<u>减少请求数</u>

* 禁用持久性购物车，因为它会增加 `customer/section/load` 请求。 请按照中的步骤操作 [永久购物车路径](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) 查看是否启用了永久购物车。
* 如果您需要重新加载或使中的内容无效 `sections.xml` 请按照中的步骤操作 [私有内容：使私有内容无效](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) 在我们的开发人员文档中。 请确保您未使用 `customerData.reload()` 方法直接包含在您的自定义设置中。
* 查看同一页面上的其他POSTAJAX请求。 在Google Chrome浏览器中打开Google Chrome开发人员工具。 单击 **网络** 选项卡，然后 **XHR** 选项卡中，将出现来自特定页面的所有AJAX请求的列表。 然后，单击每个请求，在字段中，请求方法应为GET请求。 注意：以Google Chrome为例，也可以在其他浏览器中执行此操作。
* 检查特定AJAX请求的Google标签管理器(GTM)功能。 用户可以删除此AJAX并使用私有功能重构其自定义设置，以减少向服务器发出的请求总数。
* 检查是否已启用但未使用Adobe Commerce横幅。 您可能需要 [禁用Adobe Commerce横幅输出以提高网站性能](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### 相关阅读

有关私人客户内容的更多信息，请查看 [私有内容](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) 在我们的开发人员文档中。
