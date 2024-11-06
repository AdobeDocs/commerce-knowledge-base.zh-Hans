---
title: 如何删除Magento Order Management(MOM)
description: 本文介绍了如何去掉Magento Order Management(MOM)。
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# 如何删除Magento Order Management(MOM)

1. 按照[禁用或启用集成](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration)中的步骤禁用MOM集成。
1. 按照[卸载模块](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html)中的步骤禁用MOM模块。
1. 为了提取完整的订单数据，我们提供了API。 您可以通过查看Adobe中的[订单存储库](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository)了解更多信息 | Magento包含订单信息(order_repository)的OMS文档。 在我们的Adobe中使用[规范部分](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) | MagentoOMS文档以使用其他API提取各种信息类型。
