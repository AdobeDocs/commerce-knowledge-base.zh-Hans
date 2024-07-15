---
title: 'MDVA-30565：会话缓存本地存储和签出问题'
description: MDVA-30565修补程序解决了会话缓存本地存储和签出问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。
exl-id: f0693f0c-fc6b-44af-a6a0-ebfa973bca65
feature: Cache, Checkout, Orders, Storage
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-30565：会话缓存本地存储和签出问题

MDVA-30565修补程序解决了会话缓存本地存储和签出问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6时，此修补程序可用。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.3.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当客户会话超时时，购物车页面上仍可以看到购物车项目。 这会导致估算配送方式错误，导致没有配送方式可用于访客结帐。

<u>重现步骤</u>：

1. 在Commerce管理员中启用持久性购物车。 （**启用持久性** = &quot;*是*&quot;）
1. 以前端客户的身份登录。 这将创建`persistent_shopping_cart` Cookie并启动永久会话。
1. 将产品添加到购物车。
1. 等待前端会话超时，或删除`PHPSESSID` Cookie。
1. 现在您是访客用户，但如果您转到购物车，您仍然可以看到已添加为登录客户的产品。
1. 从购物车中删除产品，现在购物车是空的。 您可以在此事件中看到Adobe Commerce删除`persistent_shopping_cart` Cookie。
1. 将新产品添加到购物车，然后转到购物车页面。
1. 现在，在浏览器控制台中，显示`V1/guest-carts/4/estimate-shipping-methods`请求现在返回404响应，消息为`{"message":"No such entity        with %fieldName = %fieldValue","parameters":{"fieldName":"cartId","fieldValue":0}}`

<u>预期的结果</u>：

预估配送方式请求返回正确结果。

<u>实际结果</u>：

估算配送方式请求失败，错误如下：“*抱歉，目前此订单没有报价单。*”

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
