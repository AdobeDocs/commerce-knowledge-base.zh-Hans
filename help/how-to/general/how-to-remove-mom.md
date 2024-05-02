---
title: 如何删除Magento Order Management(MOM)
description: 本文介绍了如何去掉Magento Order Management(MOM)。
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# 如何删除Magento Order Management(MOM)

1. 按照中的步骤禁用MOM集成 [禁用或启用集成](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration).
1. 按照中的步骤禁用MOM模块 [卸载模块](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. 为了提取完整的订单数据，我们提供了API。 您可以通过查看以下内容了解更多信息 [订单存储库](https://omsdocs.magento.com/specifications/#magento.sales.order_repository) 在我们的Adobe中 | Magento包含订单信息(order_repository)的OMS文档。 使用 [规范部分](https://omsdocs.magento.com/specifications/#services) 在我们的Adobe中 | MagentoOMS文档以使用其他API提取各种信息类型。
