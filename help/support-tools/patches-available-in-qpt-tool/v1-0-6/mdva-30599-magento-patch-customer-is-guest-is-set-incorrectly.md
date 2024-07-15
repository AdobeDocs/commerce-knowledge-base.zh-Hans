---
title: 'MDVA-30599：customer_is_guest设置不正确'
description: MDVA-30599修补程序修复了以下问题：使用API创建的访客报价错误地标记为已登录客户的报价。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6后，即可使用此修补程序。 已在Adobe Commerce 2.4.2中修复此问题。
exl-id: e16bb926-241b-451e-89a5-33000f73c5b7
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-30599：customer_is_guest设置不正确

MDVA-30599修补程序修复了以下问题：使用API创建的访客报价错误地标记为已登录客户的报价。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6时，此修补程序可用。 已在Adobe Commerce 2.4.2中修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.3.5-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.4 - 2.4.0

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用API创建的访客报价错误地标记为已登录客户的报价。

<u>重现步骤</u>：

1. 在Adobe Commerce店面，以访客用户身份将产品添加到购物车。
1. 在Adobe Commerce DB中，找到相应的`quote_id_mask`。
1. 将访客购物车的API请求发送到`quoteGuestCartRepositoryV1`购物车存储库界面。 可以通过Swagger或cURL请求来完成。

```curl
curl -X GET "http://web2-73.sparta.corp.magento.com/dev/support/ee24dev/rest/all/V1/guest-carts/ToOwPtSBxkorkCLq6ztwupPd99y8zhky" -H "accept: application/json"
```

<u>预期的结果</u>：

在响应中，您收到`"customer_is_guest": true`

<u>实际结果</u>：

在响应中，您收到`"customer_is_guest": false`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://devdocs.magento.com/cloud/project/project-patch.html)。

## 安装修补程序后所需的其他步骤

该补丁对所有新来宾购物车都有效。 如果需要修复现有来宾购物车，请为`quote.customer_id`为NULL的那些记录设置`quote.customer_is_guest = 1`。 您可以运行类似于以下内容的查询：

```sql
UPDATE quote SET customer_is_guest = 1 WHERE customer_id IS NULL;
```

>[!WARNING]
>
>我们强烈建议先在暂存/集成环境中测试查询，然后再在生产环境中运行它。 我们还建议在使用DB进行任何操作之前先备份最近的数据。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://devdocs.magento.com/quality-patches/tool.html#patch-grid)修补程序。
