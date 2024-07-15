---
title: 'MDVA-30972：订单状态错误通过REST API创建的装运'
description: MDVA-30972修补程序解决了在通过REST API创建发运期间订单状态更改不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7后，即可使用此修补程序。
exl-id: 70b8db1f-16d0-48f4-b0a2-483a7176cb89
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-30972：通过REST API创建的订单状态错误装运

MDVA-30972修补程序解决了在通过REST API创建发运期间订单状态更改不正确的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7时，此修补程序可用。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0到2.4.2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当通过REST API从管理员为具有&#x200B;*可疑欺诈*&#x200B;订单状态的订单创建部分装运时，订单状态更改为&#x200B;*正在处理*。 它应停留在&#x200B;*可疑欺诈*。

<u>先决条件</u>：

* 设置PayPal EC或其他在线支付方式。
* 设置了REST API的集成。

<u>重现步骤</u>：

1. 创建包含两个或多个项目的订单。
1. 登录到&#x200B;**管理员** > **销售** > **订单**。 打开您刚刚创建的订单。
1. 在订单详细信息页面上，向下滚动到&#x200B;**订单总计**。 单击&#x200B;**状态**&#x200B;下拉列表并选择&#x200B;*可疑欺诈*。 然后单击&#x200B;**提交评论**&#x200B;按钮。
1. 检查订单现在是否具有&#x200B;*可疑欺诈*&#x200B;状态。
1. 使用REST API从订单中创建一个物料的发运：

   ```
   * Method = `Post`
   * Header = `"{host}/rest/V1/orders/ {order_id}/ship"`
   * Body =
   ```

   ```
    {      "items": [        {          "extension_attributes": {},          "order_item_id": {order_item_id},          "qty": 1        }      ]    }
   ```

1. 再次在“管理员”中打开订单并检查其状态。

<u>预期的结果</u>：

* 订单状态= *可疑欺诈*。
* 如果从管理员创建相同的装运，则订单状态不会更改。

<u>实际结果</u>：

订单状态= *正在处理*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
