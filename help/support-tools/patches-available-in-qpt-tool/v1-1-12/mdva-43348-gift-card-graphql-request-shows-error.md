---
title: 'MDVA-43348：礼品卡GraphQL请求显示错误'
description: MDVA-43348修补程序修复了礼品卡GraphQL请求在“gift_card_options”包含“uid”时显示错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43348。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
exl-id: a9c0e1da-6698-463a-a6a8-60522f029b53
feature: Gift, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# MDVA-43348：礼品卡GraphQL请求显示错误

MDVA-43348修补程序修复了礼品卡GraphQL请求在`gift_card_options`包含“uid”时显示错误的问题。 安装[Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43348。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果gift_card_options中包含“uid”，礼品卡GraphQL请求会显示错误。

<u>重现步骤</u>：

1. 创建礼品卡产品。
1. 执行重新索引。
1. 进行GraphQL调用，其中URL键为“礼品卡”：

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) &lbrace;
  products(filter: { url_key: { eq: $urlKey } }) &lbrace;
    items &lbrace;
      id
      url_key
      ... on GiftCardProduct &lbrace;
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options &lbrace;
          uid
          title
          required
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>预期的结果</u>：

礼品卡数据会根据请求返回。

<u>实际结果</u>：

在请求礼品卡数据时出现以下错误：

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "products": &lbrace;
      "items": &lbrack;
        &lbrace;
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": &lbrack;
            null,
            null,
            null,
            null,
            null
          &rbrack;
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* 在开发人员文档中，参阅Adobe Commerce或Magento Open Source内部部署： [软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 云基础架构上的Adobe Commerce：我们的开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布高质量修补程序工具：我们支持知识库中用于自助提供高质量修补程序的新工具](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)。
* [使用我们的支持知识库中的Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查是否有针对您的Adobe Commerce问题的修补程序。

有关QPT中提供的其他修补程序的信息，请参阅我们的开发人员文档中的[QPT中提供的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)修补程序。
