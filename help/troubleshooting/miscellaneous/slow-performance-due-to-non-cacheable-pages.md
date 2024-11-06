---
title: 由于不可缓存的页面导致性能降低
description: 本文提供了解决方案，可针对任何需要缓存的页面上的任何块禁用全页缓存（例如Fastly）而增加网站加载时间或中断情况。
exl-id: 7401d9bd-710c-4221-9c3d-d78042c1c1ad
feature: Cache, Categories
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# 由于不可缓存的页面导致性能降低

本文提供了解决方案，可针对任何需要缓存的页面上的任何块禁用全页缓存（例如Fastly）而增加网站加载时间或中断情况。

## 受影响的产品和版本

* 云基础架构上的Adobe Commerce 2.x.x
* Adobe Commerce内部部署2.x.x

### 问题

网站性能缓慢，因为页面上有需要缓存但已设置为`cacheable="false"`的缓存块。

### 原因

有些页面需要由Adobe Commerce缓存。 这些页面的吞吐量最大。 对于这些类型的页面，每个请求都不会来自缓存，这会使Adobe Commerce执行速度变慢。

这些页面包括：

* 目录类别(PLP)
* 产品详细信息页面(PDP)
* 静态内容页面（主页、联系我们等）

Cacheable和uncacheable是用于指示是否应缓存页面的术语。 默认情况下，可缓存所有页面。 但是，如果布局中的任何块被指定为不可缓存，则整个页面都不可缓存。

下面的屏幕快照显示了一个设置`cacheable="false"`****的块，该块创建了一个不可缓存的页面。

![non_cacheable_kb.png](assets/non_cacheable_kb.png)

不可缓存页面的示例包括比较产品、购物车和结账页面。

不缓存以下页面列表（避免Fastly、Block和Layout缓存。） 出现这种情况是因为布局中的“可缓存”配置。

### 解决方案

检查上面指定的文件是否具有设置`cacheable="false"` 。 如果有，请检查是否需要此设置。

* 如果需要，请考虑将不可缓存的块移至[私有内容机制](https://developer.adobe.com/commerce/php/development/cache/page/private-content/)。
* 如果需要，请删除属性`cacheable="false"`并刷新布局缓存。

>[!NOTE]
>
>对于Cloud Infrastructure 2.4.1及更高版本上的Adobe Commerce，您可以使用[站点范围分析工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access)来自动检查完整页缓存配置是否正确。

### 相关阅读

在我们的开发人员文档中，[Adobe Commerce缓存概述](https://developer.adobe.com/commerce/frontend-core/guide/caching/)。
