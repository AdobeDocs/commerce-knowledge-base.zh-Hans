---
title: Adobe Commerce 2.4.1顶点地址验证消息地址更新
description: 本文介绍了一个已知的Adobe Commerce 2.4.1问题，其中在使用与帐单地址不同的送货地址时，在付款步骤中无法验证顶点地址。 Adobe Commerce 2.4.2中计划修复此问题。
exl-id: c2abeb96-e837-4d16-92dd-82fea5661dd9
feature: Shipping/Delivery
role: Developer
source-git-commit: ce377064efabaf09d3856da7c6c5c742a9fdcc2f
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Adobe Commerce 2.4.1顶点地址验证消息地址更新

本文介绍了一个已知的Adobe Commerce 2.4.1问题，其中在使用与帐单地址不同的送货地址时，在付款步骤中无法验证顶点地址。 Adobe Commerce 2.4.2中计划修复此问题。

## 受影响的产品和版本

* 启用了顶点集成的Adobe Commerce内部部署2.4.1
* 云基础架构2.4.1上的Adobe Commerce启用了顶点集成

## 问题


<u>要再现的步骤：</u>

1. 创建帐户并登录。
1. 通过单击&#x200B;**添加到购物车**&#x200B;将项目添加到购物车。 单击“购物车”图标，然后单击&#x200B;**继续结帐**。
1. 在&#x200B;**送货地址**&#x200B;字段中输入有效地址。
1. 检查&#x200B;**配送方式**&#x200B;下的选项之一。 然后单击&#x200B;**下一步**。
1. 如果地址验证建议不同的地址信息，请单击&#x200B;**更新地址**，然后单击&#x200B;**下一步**。
1. 取消选中&#x200B;**我的帐单和送货地址相同**&#x200B;复选框。

<u>第一个方案：</u>

请按照上述[执行六个步骤](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth)，然后：

1. 输入新的有效帐单地址。
1. 单击&#x200B;**更新**&#x200B;按钮。 它将显示如下消息/建议： *地址无效。*&#x200B;下面将提供地址建议，如： *邮政编码： XXXXX- XXXX Street ： XXX City Street XXX*
1. 单击&#x200B;**更新**&#x200B;按钮（请勿单击Vertex地址建议的&#x200B;**更新地址**&#x200B;按钮）。
1. 单击已更新帐单地址的&#x200B;**编辑**&#x200B;按钮。
1. 从地址下拉列表中选择地址。
1. 单击&#x200B;**更新**&#x200B;按钮。

<u>预期结果：</u>

旧的验证消息/建议消息被删除。

<u>实际结果：</u>

验证消息/建议&#x200B;*“我们找不到有效的地址邮政编码： XXXXX-XXXX Street ： XXX City street XXX”*&#x200B;消息为&#x200B;**未删除**。 如果您在表单中输入的地址无效，也会出现同样的问题。

<u>第二个方案：</u>

请按照上述[执行六个步骤](/help/troubleshooting/miscellaneous/magento-2-4-1-vertex-address-validation-message-post-address-update.md#first_sixth)，然后：

1. 使用有效地址填写地址表单。
1. 单击&#x200B;**更新**&#x200B;按钮。 它将显示如下消息/建议： *地址无效。*&#x200B;下面将提供一个地址建议，如： *邮政编码： XXXXX-XXXX Street ： XXX City Street XXX*。
1. 单击&#x200B;**更新**&#x200B;按钮（请勿单击顶点地址建议的&#x200B;**更新地址**&#x200B;按钮）。
1. 检查&#x200B;***我的帐单和送货地址是否相同***&#x200B;下拉列表。

<u>预期结果：</u>

旧的验证消息/建议消息被删除。

<u>实际结果：</u>

验证消息/建议&#x200B;*“我们找不到有效的地址邮政编码： XXXXX-XXXX Street XXX City street XXX”*&#x200B;消息为&#x200B;**未删除**。 如果您在表单中输入的地址无效，也会出现同样的问题。

## 我们的支持知识库中的相关阅读：

[Adobe Commerce 2.3.6、2.4.0-p1和2.4.1已知问题：启用帐户后无法登录dotdigital](/help/troubleshooting/miscellaneous/magento-2-3-6-2-4-0-p1-2-4-1-known-issue-dotdigital-login.md)
