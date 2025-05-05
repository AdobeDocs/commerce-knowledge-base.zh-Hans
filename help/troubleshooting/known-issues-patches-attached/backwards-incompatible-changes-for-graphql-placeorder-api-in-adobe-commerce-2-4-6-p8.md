---
title: '''在Adobe Commerce 2.4.6-p8中， [!DNL GraphQL] ''placeOrder'' [!DNL API] 的向后不兼容更改'''
promoted: true
description: 本文为已知的Adobe Commerce版本2.4.6-p8 Cloud和内部部署问题提供了一个修补程序，该问题导致“placeOrder” [!DNL GraphQL API] 未返回预期的错误响应，如以前的2.4.6修补程序版本中所示。 对于使用PWA店面或其商店的任何其他基于 [!DNL GraphQL API]的店面的商家，这可能会导致结账体验受损。
feature: Checkout, REST, GraphQL
role: Developer
source-git-commit: 01b79c75df34de20f1ff50ab40c0a8d608ffa779
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Adobe Commerce 2.4.6-p8中[!DNL GraphQL] `placeOrder` [!DNL API]的向后不兼容更改

本文为已知的Adobe Commerce版本2.4.6-p8 Cloud和内部部署问题提供了一个修补程序，该问题导致`placeOrder` [!DNL GraphQL API]未返回预期的错误响应，如以前的2.4.6修补程序版本中所示。 对于使用[!DNL PWA]店面或其商店的任何其他基于[!DNL GraphQL API]的店面的商家，这可能会导致结账体验中断。

>[!NOTE]
>
>如果您在应用修补程序时遇到任何问题，请联系支持服务。

## 受影响的产品和版本

* Cloud 2.4.6-p8上的Adobe Commerce
* Adobe Commerce内部部署2.4.6-p8

## 问题

在Adobe Commerce 2.4.6-p8仅安全修补程序上升级后，[`placeOrder` [!DNL GraphQL API]](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)不会返回预期的错误响应，任何以前的2.4.6修补程序版本中都会看到此响应。 对于使用[!DNL PWA]店面或其商店的任何其他基于[!DNL GraphQL API]的店面的商家，这可能会导致结账体验中断。

<u>要再现的步骤</u>：

运行`placeOrder` [!DNL GraphQL]请求，您认为该请求会出现错误响应。

<u>预期的结果</u>：

您会收到预期的错误响应。

<u>实际结果</u>：

您收到的不是预期的错误响应，而是成功的响应，但具有新的`errors`密钥，如下所示：

```
{
    "data": {
        "placeOrder": {
            "order": null,
            "__typename": "PlaceOrderOutput"
        }
    }
}
```

## 适用于Adobe Commerce on Cloud和Adobe Commerce内部部署软件的解决方案

要解决此问题，请应用修补程序。
要下载它，请单击以下链接：

[ac-13283-composer-patch.zip](assets/ac-13283-composer-patch.zip)

## 如何应用修补程序

解压缩文件，并参阅我们的支持知识库中的[如何应用Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=zh-Hans)提供的编辑器修补程序以获取说明。

## 仅适用于Adobe Commerce on Cloud商家 — 如何判断是否已应用修补程序

考虑到无法轻松检查问题是否已修补，您可能需要检查修补程序是否已成功应用。

<u>您可以执行以下步骤，以样例文件`VULN-27015-2.4.7_COMPOSER.patch` **为例</u>**：

1. [安装 [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans)。
1. 运行命令： <br>
   ![ac-13283-tell-if-patch-applied-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. 您应该会看到类似以下内容的输出，其中VULN-27015返回&#x200B;*已应用*&#x200B;状态：

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

