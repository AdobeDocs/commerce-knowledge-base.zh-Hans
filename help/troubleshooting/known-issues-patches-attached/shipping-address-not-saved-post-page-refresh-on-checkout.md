---
title: 结帐后刷新页面时未保存送货地址
description: 本文为已知的Adobe Commerce 2.2.3问题提供了一个修补程序，该问题导致客户在来宾结账时刷新浏览器页面后，已填充的送货地址表单再次为空。 启用永久购物车时出现问题。
exl-id: b757e4af-7b1a-41bc-8460-9a6858c7aa5e
feature: Checkout, Orders, Shipping/Delivery
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 结帐后刷新页面时未保存送货地址

本文为已知的Adobe Commerce 2.2.3问题提供了一个修补程序，该问题导致客户在来宾结账时刷新浏览器页面后，已填充的送货地址表单再次为空。 启用永久购物车时出现问题。

## 问题

客户通过访客结账并完成所有表单，包括送货地址。 他们转到复查和支付部分并重新加载页面。 表单为空，他们需要重新输入送货地址。 已启用永久购物车功能。

<u>重现问题的步骤</u> ：

**先决条件**：已启用永久购物车功能。 检查是否已在Admin中的&#x200B;**商店** > **配置** > **客户**&#x200B;或&#x200B;**商店** > **配置** > **销售，**&#x200B;下启用它，具体取决于您的Adobe Commerce版本。

1. 去店面。
1. 将产品添加到购物车。
1. 以来宾身份继续结帐。
1. 填写送货地址，选择送货选项，然后继续确保付款。
1. 重定向至“结账的审核和支付”部分。
1. 仔细检查您是否在“收货地址”部分中看到了送货地址。
1. 刷新页面。

<u>预期的结果</u>：

您可以继续结帐，所有数据都会被保存。

<u>实际结果</u>：

送货地址为空，需要租赁。

## Patch

该修补程序已附加到本文。 要下载它，请向下滚动到文章的结尾并单击文件名，或单击以下链接：

[下载MDVA-9718\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-9718_EE_2.2.3_COMPOSER_v1.patch.zip)

### 兼容的Adobe Commerce版本

**已为**&#x200B;创建修补程序

* Adobe Commerce 2.2.3

**该修补程序与以下Adobe Commerce版本也兼容（但可能无法解决此问题）：**

* 云基础架构上的Adobe Commerce 2.1.13 - 2.1.18
* 云基础架构上的Adobe Commerce 2.2.0 - 2.2.5
* Adobe Commerce内部部署2.0.X
* Adobe Commerce内部部署2.1.X
* Adobe Commerce内部部署2.2.0 - 2.2.2和2.2.4 - 2.2.5

## 如何应用修补程序

有关说明，请参阅我们的支持知识库中的[如何应用Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md)提供的编辑器修补程序。

## 附加文件
