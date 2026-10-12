---
title: 如何删除Magento Order Management (MOM)
description: 本文介绍了如何删除Magento Order Management (MOM)系统。
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%
---
# 如何删除Magento Order Management (MOM)

1. 按照[禁用或启用集成](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration)中的步骤禁用MOM集成。
1. 按照[卸载模块](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html?lang=zh-Hans)中的步骤禁用MOM模块。
1. 为了提取完整的订单数据，我们提供了API。 您可以通过查看Adobe中的[订单存储库](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository)了解更多信息 | Magento OMS文档，其中涵盖订单信息(order_repository)。 使用我们Adobe中的[规范部分](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) | Magento OMS文档以使用其他API提取不同的信息类型。
