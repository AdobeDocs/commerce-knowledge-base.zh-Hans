---
title: 网站和API性能低
description: 本文为云基础架构2.2.1上的已知Adobe Commerce问题提供了一个修补程序，该问题与由于写入“debug.log”所需的时间过长而导致的站点和API性能较低有关。
exl-id: b71816cd-f580-4c80-9694-585ed051a56d
feature: REST, Observability
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# 网站和API性能低

本文为云基础架构2.2.1上已知的Adobe Commerce问题提供了一个修补程序，该问题与写入`debug.log`所需的长时间导致的站点和API性能较低有关。

## 问题

站点性能缓慢。 API操作运行缓慢，例如使用`PUT`方法更新产品。 当您更仔细地查看使用New Relic的操作时，大多数内存和CPU都通过写入`/var/log/debug.log`来消耗。

## 解决方案

要解决此问题，请应用修补程序。 该修补程序将拆分日志、付款和传送方法日志，并将其写入不同的文件。

## Patch

该修补程序已附加到本文。 要下载该文件，请向下滚动到文章的结尾，然后单击文件名或单击以下链接：

[下载MDVA-8371\_EE\_2.2.1\_COMPOSER\_v2.patch](assets/MDVA-8371_EE_2.2.1_COMPOSER_v2.patch.zip)

### 兼容的Adobe Commerce版本

该修补程序是为以下对象创建的：

* 云基础架构上的Adobe Commerce 2.2.1

该修补程序与以下Adobe版本也兼容（但可能无法解决此问题）：

* 云基础架构上的Adobe Commerce 2.2.0、2.2.2、2.2.3
* Adobe Commerce内部部署2.2.0、2.2.2、2.2.3

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
